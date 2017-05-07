---
layout: post
title:  "Linux文件权限与目录配置"
categories: Linux
tags:  Linux
author: zer0w0lf
---

* content
{:toc}

Linux文件权限以及目录配置。


## 用户身份及用户组记录文件

- /etc/passwd: 用户身份信息
- /etc/shadow: 用户密码信息
- /etc/group: 用户组信息

## 文件属性

-rw-r--r-- 1 root root 1113 3月  30 02:10 /etc/group

- 文件类型及权限: -rwxr--r--
  > * 类型 d目录、-文件、l链接文件、b块设备文件、c字符设备文件
- 链接数：有多少个文件名链接到此节点
- 文件所有者
- 文件所属用户组
- 文件容量大小，单位B
- 创建日期或最后修改时间
- 文件名，.开头为隐藏文件

## info page

info page将文件数据拆成一个个段落，每个段落为node，有自己的页面，可以通过类似网页超链接方式来跳转

## 开关机

- 先查询用户 who；网络状态 netstat -a；后台进程 ps -aux
- 通知在线用户关机 shutdown -k “will shutdown”
- 数据同步写入硬盘 sync
- 关机命令 shutdown
- 重启关机 reboot halt poweroff
- 可以通过init 0关机、或init 6重启



