---
title: 【原创】关于git操作
date: 2017-10-20 11:09:58
tags:
---
### 一、误操作git pull之后如何撤销？
1、git reflog命令查看历史变更记录
2、git reset --hard HEAD@{n}，（n是要回退到的引用位置）回退。
### 二、git回滚
1、git log    查看提交的日志，找到要回滚的commit编号，比如：e377f60e28c8b84158
2、git reset --hard e377f60e28c8b84158    回滚
3、git push -f origin master   强制提交
