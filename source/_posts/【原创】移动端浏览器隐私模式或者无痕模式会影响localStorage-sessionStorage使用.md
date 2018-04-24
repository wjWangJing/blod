---
title: 【原创】移动端浏览器隐私模式或者无痕模式会影响localStorage/sessionStorage使用
date: 2017-08-29 17:52:51
tags:
---
### 前言
> 有没有被某些浏览器的隐私模式搞懵过？隐私模式会导致各种各样的问题，比如常用的本地存储localStorage/sessionStorage

<!--more-->
&emsp;&emsp;新项目中有需求用到了sessionStorage，但是在一些手机里一遇到和sessionStorage相关的代码就不执行，这给我急的，然后调试了一下发现是手机开启了无痕模式浏览，影响了sessionStorage的使用。
&emsp;&emsp;找到了问题的根源，那剩下的事情就是解决了：总结来说就是在移动使用sessionStorage或者localStorage时，首先要判断是否支持，或者说是否被禁用，如果支持（或者没有被禁用），那么可以直接使用，如果被禁用了，可能就要换一种方式了。
&emsp;&emsp;判断方法如下：
```
function isStorageSupported() {
    try {
        window.sessionStorage.setItem(key, 'test');
        return true;
    } catch (error) {
        return false;
    }
}
```
