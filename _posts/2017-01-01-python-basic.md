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


## 数据类型

```python
#变量不需要事先声明，在赋值时自动确定类型
a = 10

#查看变量的类型使用type函数
print(type(a))

#基本数据类型
a = 10         # int 整数
a = 1.3        # float 浮点数
a = True       # 真值 (True/False)
a = 'Hello!'   # 字符串。字符串也可以用双引号。

#序列(sequence)：有顺序的对象元素的集合，可以没有对象元素或包含一个或多个对象元素，序列有元组和列表两种
#元组(tuple)：也称为定值表，对象元素以()包含，一旦建立，各个对象元素不可再变更
s1 = (2, 1.3, 'love', 5.6, 9, 12, False)         # s1是一个tuple
#列表(list):对象元素以[]包含，各个对象元素可以再变更
s2 = [True, 5, 'smile']                          # s2是一个list
#序列中单个元素对象引用：序列的引用通过s[<int>]实现，int为下标，下标从0开始
print(s1[0])
#序列的范围引用：基本样式[下限:上限:步长]。范围引用时如果写明上限，那么这个上限本身不包括在内
print(s1[:5])             # 从开始到下标4 （下标5的元素 不包括在内）
print(s1[2:])             # 从下标2到最后
print(s1[0:5:2])          # 从下标0到下标4 (下标5不包括在内)，每隔2取一个元素 （下标为0，2，4的元素）
print(s1[2:0:-1])         # 从下标2到下标1
#尾部元素引用
print(s1[-1])             # 序列最后一个元素
print(s1[-3])             # 序列倒数第三个元素

```


## 类（class）

类的定义及对象创建和属性引用如下：

```python
#类的定义
class Classname(name):
    #属性
    attribute1 = "xxx"
    attribute2 = "yyy" 
    
    #特殊方法
    def __init__(self, default_words):
        print 'Hello, ', default_words
    
    #一般方法
    def method1(self, x, y):
        # ......
    def method2(self, a, b):
        # ......
    
    #通过self调用类的属性和方法
    def method3(self):
        print self.attribute1
    def method4(self):
        self.method3

#创建对象
objectname = Classname()

#引用对象的属性
objectname.attribute
```

说明：

- name：当name为“object”时，表示该类没有父类；当name为父类名称时，则定义的为父类的子类，即子类继承父类(inheritance)，子类继承父类的所有属性和方法
- self：类中定义的方法第一个参数必须为self，代表了根据类定义而创建的对象，可以通过self调用类的属性和方法。**可以通过对象修改类的属性值，但这很危险，类属性值的改变会影响类的所有对象**
- 特殊方法：以“\_\_”开头的方法为特殊方法(special method)，\_\_init\_\_()特殊方法在创建对象时会自动调用该方法，此过程也叫初始化