---
layout: post
title:  "正则表达式"
categories: RegExp
tags:  Regular
author: zer0w0lf
---

* content
{:toc}

正则表达式基础。

## 单个字符

| 字符     | 描述                                                                                      |
|----------|-------------------------------------------------------------------------------------------|
| 字符本身 | 匹配任意字符本身                                                                          |
| .        | 匹配除 "\n" 之外的任何单个字符。要匹配包括 '\n' 在内的任何字符，请使用象 '[.\n]' 的模式。 |
| x|y      | 匹配 x 或 y。例如，'z|food' 能匹配 "z" 或 "food"。'(z|f)ood' 则匹配 "zood" 或 "food"。    |
| [xyz]    | 字符集合。匹配所包含的任意一个字符。例如， '[abc]' 可以匹配 "plain" 中的 'a'。            |

***

[Python标准库01 正则表达式](http://www.cnblogs.com/vamei/archive/2012/08/31/2661870.html)

[深入理解正则表达式](http://www.cnblogs.com/China3S/archive/2013/11/30/3451971.html)

[正则表达式全部符号解释](http://www.cnblogs.com/yirlin/archive/2006/04/12/373222.html)

