---
title: 【原创】在mac上如何用safari调试ios手机的移动端页面
date: 2017-08-28 14:38:49
tags:
---
### 前言
> 移动端网页调试比较麻烦，在此记录一种方法，方便查找

<!--more-->
### 第一步：打开iphone手机的开发者模式，流程是：【设置】->【Safari】->【高级】->开启【Web检查器】 ，如图1、图2
![图1](https://eternal-blog.oss-cn-beijing.aliyuncs.com/blog/pic-1.jpg?Expires=1524540633&OSSAccessKeyId=TMP.AQGzY87mNUovU8LV8U4kgzo6MR2EIAGVKNjoWPNxxaqaXRkEGdZ8QsCjDHw2MC4CFQDpn0gWQe5Q4LkUFvKBZ-mlW7ZRYQIVALmsjJh6xMFVtDAkWvAvlAPOjZlq&Signature=WQAgysmAb3%2BQc4u8X%2FBTqKk6V8U%3D)
![图2](https://eternal-blog.oss-cn-beijing.aliyuncs.com/blog/pic-2.jpg?Expires=1524540697&OSSAccessKeyId=TMP.AQGzY87mNUovU8LV8U4kgzo6MR2EIAGVKNjoWPNxxaqaXRkEGdZ8QsCjDHw2MC4CFQDpn0gWQe5Q4LkUFvKBZ-mlW7ZRYQIVALmsjJh6xMFVtDAkWvAvlAPOjZlq&Signature=5K0cQ6ey9vTZhEQ%2FdCmKBwZGnb0%3D)
### 第二步：打开Mac上Safari的开发者模式，流程是【Safari】->【偏好设置】->【高级】->【在菜单栏中显示“开发”菜单】勾选
![图3](https://eternal-blog.oss-cn-beijing.aliyuncs.com/blog/pic-3.jpg?Expires=1524540707&OSSAccessKeyId=TMP.AQGzY87mNUovU8LV8U4kgzo6MR2EIAGVKNjoWPNxxaqaXRkEGdZ8QsCjDHw2MC4CFQDpn0gWQe5Q4LkUFvKBZ-mlW7ZRYQIVALmsjJh6xMFVtDAkWvAvlAPOjZlq&Signature=vChrCMZ41NJzUcaFP5Ak1CUusa8%3D)
### 第三步：用数据线将iphone手机和mac连接起来，在电脑的safari中按照流程执行：【开发】->【手机名称】->【正在调试的网站】
![图4](https://eternal-blog.oss-cn-beijing.aliyuncs.com/blog/pic-4.jpg?Expires=1524540718&OSSAccessKeyId=TMP.AQGzY87mNUovU8LV8U4kgzo6MR2EIAGVKNjoWPNxxaqaXRkEGdZ8QsCjDHw2MC4CFQDpn0gWQe5Q4LkUFvKBZ-mlW7ZRYQIVALmsjJh6xMFVtDAkWvAvlAPOjZlq&Signature=z529hKYEl2f7cIKh61x2Uc%2FaFmY%3D)
### 最后，就可以按照调试pc端页面的思路来调试ios的页面了
