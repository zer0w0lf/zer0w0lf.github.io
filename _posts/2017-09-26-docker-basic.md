---
layout: post
title:  "Docker基础知识"
categories: Docker
tags:  Docker install command
author: zer0w0lf
---

* content
{:toc}

Docker基础知识介绍，包括基本安装和使用。
![Docker和虚拟机的区别](http://img.blog.csdn.net/20141225001257949?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvZGVscGhpd2Nkag==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

## 基础命令

- date: 显示日期与时间
- cal: 显示日历
- bc: 计算器

## man page(操作说明)

- man 7 man: 可以参考man命令详细的说明，特别是每个命令的数字解释
  > * /string 向下查询string字符串
  > * ?string 向上查询string字符串
  > * n N 结合以上两个命令向上或向下查询
- man -f man：取得更多与man相关的信息
- man -k man：在系统说明文件中，只要有man关键字的就将该说明列出来

## info page

info page将文件数据拆成一个个段落，每个段落为node，有自己的页面，可以通过类似网页超链接方式来跳转

## 开关机

- 先查询用户 who；网络状态 netstat -a；后台进程 ps -aux
- 通知在线用户关机 shutdown -k “will shutdown”
- 数据同步写入硬盘 sync
- 关机命令 shutdown
- 重启关机 reboot halt poweroff
- 可以通过init 0关机、或init 6重启



