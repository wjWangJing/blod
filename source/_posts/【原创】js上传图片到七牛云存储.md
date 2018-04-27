---
title: 【原创】js上传图片到七牛云存储
date: 2017-08-29 17:24:43
tags:
---
### 前言
> 项目开发过程中遇到一个需求，运营人员需要上传图片到七牛云，最开始的做法是，后台对接七牛，然后出一个接口，前端调用接口，先将图片传到后台，然后后台再上传七牛云，用的过程中发现，图片小的情况下还好，图片一旦到了几十兆甚至几百兆的时候就很慢，前端上传图片到后台需要一定时间，后端上传到七牛又需要一段时间，很是麻烦，所以果断改成了前端直接上传七牛

<!--more-->
&emsp;&emsp;直接上代码
```
<!doctype html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>js上传图片到七牛</title>
    <style>
        #container{
            width:200px;
            height:200px;
            border:1px solid #9d9d9d;
            border-radius: 6px;
            margin:50px auto;
            position: relative;
            overflow: hidden;
        }
        .upload-progress{
            width:100%;
            height:100%;
            position: absolute;
            top:0;
            left:0;
            background: rgba(0,0,0,0.5);
            z-index: 5;
            color:#fff;
            line-height: 200px;
            text-align: center;
            display: none;
        }
        #uploadImage{
            width:100%;
            height:100%;
            position: absolute;
            top:0;
            left:0;
            z-index: 2;
            text-align: center;
            line-height: 200px;
            cursor: pointer;
        }
        #container img{
            width:100%;
            position: absolute;
            top:0;
            left:0;
            z-index: 1;
        }
    </style>
</head>
<body>
<div id="container">
    <div id="uploadImage">选择文件</div>
    <div class="upload-progress"></div>
</div>

<script src="/moxie.js"></script>
<script src="/plupload.min.js"></script>
<script src="/qiniu.js"></script>
<script>
    var uploader = Qiniu.uploader({
        disable_statistics_report: false,                                   // 禁止自动发送上传统计信息到七牛，默认允许发送
        runtimes: 'html5,flash,html4',                                      // 上传模式，依次退化
        browse_button: 'uploadImage',                                       // 上传选择的点选按钮，必需
        container: 'container',                                             // 上传区域DOM ID，默认是browser_button的父元素
        max_file_size: '100mb',                                             // 最大文件体积限制
        flash_swf_url: 'Moxie.swf',                                         // 引入flash，相对路径
        dragdrop: false,                                                    // 关闭可拖曳上传
        chunk_size: '4mb',                                                  // 分块上传时，每块的体积,如果遇到分辨率特别高的图片不能采用分片上传，此时该值应该设置为0
        multi_selection: !(moxie.core.utils.Env.OS.toLowerCase() === "ios"),
        uptoken_url: 'XXX',                                                 // 在初始化时，uptoken，uptoken_url，uptoken_func三个参数中必须有一个被设置,uptoken是上传凭证，由其他程序生成;uptoken_url是提供了获取上传凭证的地址，如果需要定制获取uptoken的过程则可以设置uptoken_func;其优先级为uptoken > uptoken_url > uptoken_func
        domain: 'XXX',                                                      // bucket域名，下载资源时用到，必需
        get_new_uptoken: true,                                              // 设置上传文件的时候是否每次都重新获取新的uptoken
        auto_start: true,                                                   // 选择文件后自动上传，若关闭需要自己绑定事件触发上传
        max_retries: 3,                                                     // 上传失败最大重试次数
        save_key: true,
        resize: {                                                           // 想限制上传图片尺寸，直接用resize这个属性
            width: 300,
            height: 300
        },
        init: {
            'FilesAdded': function(up, files) {                             // 文件添加进队列后，处理相关的事情
                plupload.each(files, function(file) {
                    console.log(file)
                });
            },
            'BeforeUpload': function(up, file) {                            // 每个文件上传前，处理相关的事情
                console.log("开始上传之前");
                $(".upload-progress").show();
            },
            'UploadProgress': function(up, file) {                          // 每个文件上传时，处理相关的事情
                console.log("上传中");
                $(".upload-progress").html("上传进度:"+file.percent + "%");
            },
            'FileUploaded': function(up, file, info) {                       // 每个文件上传成功后，处理相关的事情
                console.log("上传成功");
                $(".upload-progress").hide();
                var img = new Image();                                      //创建一个Image对象，实现图片的预下载
                img.src = "http://qiniu.com/"+res.key;
                $("#container").append(img);
            },
            'Error': function(up, err, errTip) {
                console.log("上传出错")
            },
            'UploadComplete': function() {
                //队列文件处理完毕后，处理相关的事情
            }
        }
    });
</script>
</body>
</html>
```
**需要注意的是：
1、这个uploader初始化的时候如果放在change事件中是不会执行的
2、分块上传时，一些分辨率或者色彩密度较高的图片不支持切片
3、点击选择文件之后函数不执行的原因可能有：1）browse_button和container的值写成了class，但是不支持class，需要改成id名；2）函数没有初始化；3）后台返回来的token字段不正确，如果是这个原因，可以尝试将token改为uptoken**
最后附上[七牛官方的上传demo](http://jssdk.demo.qiniu.io/?ref=developer.qiniu.com)
