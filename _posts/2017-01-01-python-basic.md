---
layout: post
title:  "Python基础知识"
categories: Python
tags:  Python Class Module
author: zer0w0lf
---

* content
{:toc}

Python基础知识介绍，总结基本概念以及相应的注意点。

![](http://pic.58pic.com/58pic/12/40/48/158PICT58PICEQt.jpg)




## 类（class）

类的定义如下：

```python
class Classname(name):
    attribute1 = "xxx"
    attribute2 = "yyy" 
    def method1(self, x, y):
        # ......
    def method2(self, a, b):
        # ......
```

说明：

- name：当name为“object”时，表示该类没有父类；当name为父类名称时，则定义的为父类的子类
- self：类中定义的方法第一个参数必须为self

