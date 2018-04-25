---
title: 【原创】hexo系列问题
date: 2018-04-25 11:08:39
tags:
---
### 前言
> 用hexo搞了个自己的博客，顺便记录一下自己踩过的坑

<!--more-->
### 一、hexo系列问题之部署到github时会删掉README文件
#### 1、首先，先来看一下为什么部署之后会删掉README文件：
&emsp;&emsp;在编辑完博客内容之后，我们会先执行命令hexo g来生成静态文件，此时会把source文件里的.md格式的文件渲染为html文件并放到public下面，接下来执行命令hexo d，会把public下面的所有文件提交到对应的XXX.github.io这个仓库；但是README.md并没有出现在public中，所以github会认为我们删掉了README文件
#### 2、填坑
&emsp;&emsp;1）我们在本地的source文件里新建一个README.md文件。
&emsp;&emsp;2）修改Hexo根目录下的_config.yml文件，将skip_render参数的值设置为README.md
> 加上第二步这个设置，是为了告诉hexo的解析器，在渲染source文件里的md文件时，跳过README.md文件
### 二、hexo首页文章显示查看原文按钮
&emsp;&emsp;在文章中添加如下格式：
```
这是摘要
<!-- more -->
 这是全文
```
* 需要注意的是，点击 《阅读全文》 之后，文章会自动定位到所在位置，想要修改成从头阅读需要修改_config.yml 文件：
```
scroll_to_more: false
```
