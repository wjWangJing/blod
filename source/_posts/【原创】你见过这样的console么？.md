---
title: 【原创】你见过这样的console么？
date: 2018-05-04 14:43:50
tags:
---
### 前言
> console是前端开发中常用的调试方法，但是你见过这种样式的console么？

<!--more-->
&emsp;&emsp;比如这样的：
![图](https://eternal-blog.oss-cn-beijing.aliyuncs.com/blog/pic-17.jpg)

或者这样的：
![图](https://eternal-blog.oss-cn-beijing.aliyuncs.com/blog/pic-18.jpg)

又或者这样的：
![图](https://eternal-blog.oss-cn-beijing.aliyuncs.com/blog/pic-19.jpg)

这种带着css样式的console是不是看起来更好一点。
其实实现方法很简单：格式如下：
```
console.log("%c需要输出的信息 ", "css 代码");
```
可以复制以下代码到控制台自己试一下：
```
console.log("%cHello World", "font-size:30px;padding:10px;color: #fff;text-transform: uppercase;text-shadow:0 0 5px #fff,0 0 10px #fff, 0 0 15px #fff, 0 0 40px #ff00de, 0 0 70px #ff00de; ");
```
当然，如果有足够的时间，可以加上上面这些效果，给console添一点乐趣，毕竟，有时候开发也是很无聊的。但是大部分时候，没有时间去搞这些花里胡哨的东西，在日常开发中，用的最多的就是console.log()，输出的信息多了，很容易看晕，毕竟，我就是经常干这种事情的人，emmm。。
所以说如果能让自己输出的信息变得可读性高一点，岂不是很好。
比如：可以用console.warn()输出警告信息：
![图](https://eternal-blog.oss-cn-beijing.aliyuncs.com/blog/pic-20.jpg)
可以用console.error()输出错误信息：
![图](https://eternal-blog.oss-cn-beijing.aliyuncs.com/blog/pic-21.jpg)
可以用console.info()输出多个对象信息：
![图](https://eternal-blog.oss-cn-beijing.aliyuncs.com/blog/pic-22.jpg)
可以用console.table()将数据输出成表格：
![图](https://eternal-blog.oss-cn-beijing.aliyuncs.com/blog/pic-23.jpg)

开发的时候加上这些是不是能添点乐趣？
最后再补上[MDN文档](https://developer.mozilla.org/zh-CN/docs/Web/API/Console)
