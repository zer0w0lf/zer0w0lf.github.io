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

## 运算

```python
#数学运算
print 1+9        # 加法
print 1.3-4      # 减法
print 3*5        # 乘法
print 4.5/1.5    # 除法
print 3**2       # 乘方     
print 10%3       # 求余数

#判断：判断是真还是假，返回True/False
print 5==6               # ==， 相等
print 8.0!=8.0           # !=, 不等
print 3<3, 3<=3          # <, 小于; <=, 小于等于
print 4>5, 4>=0          # >, 大于; >=, 大于等于
print 5 in [1,3,5]       # 5是list [1,3,5]的一个元素

#逻辑运算：True/False之间的运算
print True and True, True and False      # and, “与”运算， 两者都为真才是真
print True or False                      # or, "或"运算， 其中之一为真即为真
print not True                           # not, “非”运算， 取反
```

## 条件与循环
```python
#if条件语句：以四个空格的缩进来表示隶属关系, Python中不能随意缩进
if  <条件1>:
    statement
elif <条件2>:
    statement
elif <条件3>:
    statement
else:
    statement

#for循环：需要预先设定好循环的次数(n)，然后执行隶属于for的语句n次
for element in sequence:   #每次从sequence中取出一个元素赋值给element，然后执行statement
    statement

#while循环：不停地循环执行隶属于它的语句，直到条件为假(False)
while condition:
    statement

#中断循环
continue   # 在循环的某一次执行中，如果遇到continue, 那么跳过这一次执行，进行下一次的操作
break      # 停止执行整个循环
```
## 函数
```python
#函数定义
def function_name(para1, para2, para3):  #函数参数不是必须的
    statement
    return something  #return并不是必须的，当没有return, 或者return后面没有返回值时，函数将自动返回None。return可以返回多个值，以逗号分隔，如return a,b,c，相当于返回一个tuple(定值表)

#函数调用：基本数据类型的参数通过值传递，不影响原来的变量；表类型的参数通过指针传递，影响原来的变量
a = 1

def change_integer(a):
    a = a + 1
    return a

print change_integer(a)
print a   #a的值为1，保持不变

#===(Python中 "#" 后面跟的内容是注释，不执行 )

b = [1,2,3]

def change_list(b):
    b[0] = b[0] + 1
    return b

print change_list(b)
print b    #列表b的值发生变化
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