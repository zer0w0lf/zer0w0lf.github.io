---
layout: post
title:  "Python进阶"
categories: Python
tags:  Python Class Module
author: zer0w0lf
---

* content
{:toc}

Python进阶知识总结。

## 特殊方法

特殊方法又被成为魔法方法(magic method)，方法名的前后各有两个下划线，特殊方法定义了许多Python语法和表达方式，当对象中定义了特殊方法的时候，Python也会对它们有“特殊优待”。

运算符是通过调用对象的特殊方法实现的

```python
'abc' + 'xyz'               # 连接字符串

# 以上运算符实际执行以下操作
'abc'.__add__('xyz')
```

许多内置函数也都是调用对象的特殊方法

```python
len([1,2,3])      # 返回表中元素的总数

# 实际上执行如下操作
[1,2,3].__len__()
```

任何一个有__call__()特殊方法的对象都被当作是函数。

```python
class SampleMore(object):
    def __call__(self, a):
        return a + 5

add = SampleMore()     # A function object
print(add(2))          # Call function    
map(add, [2, 4, 5])    # Pass around function object
```

***

## 上下文管理器

上下文管理器(context manager)用于规定某个对象的使用范围。一旦进入或者离开该使用范围，会有特殊操作被调用(比如为对象分配或者释放内存)。语法形式为 with EXPR as VAR，执行流程如下：

```python
# with EXPR as VAR:

VAR = EXPR
VAR = VAR.__enter__()
try:
    BLOCK
finally:
    VAR.__exit__()
```

如下代码段解析：使用上下文管理器的语法时，实际上要求Python在进入程序块之前调用对象的\_\_enter\_\_()方法，在结束程序块的时候调用\_\_exit\_\_()方法。对于文件对象f来说，它定义了\_\_enter\_\_()和\_\_exit\_\_()方法(可以通过dir(f)看到)。在f的\_\_exit\_\_()方法中，有self.close()语句。所以在使用上下文管理器时，就不用明文关闭f文件了。

```python
# with context manager
with open("new.txt", "w") as f:
    print(f.closed)
    f.write("Hello World!")
print(f.closed)
```

任何定义了__enter__()和__exit__()方法的对象都可以用于上下文管理器。

```python
# customized object

class VOW(object):
    def __init__(self, text):
        self.text = text
    def __enter__(self):
        self.text = "I say: " + self.text    # add prefix
        return self                          # note: return an object
    def __exit__(self,exc_type,exc_value,traceback):
        self.text = self.text + "!"          # add suffix


with VOW("I'm fine") as myvow:
    print(myvow.text)

print(myvow.text)
```

***

## 对象的属性

每个对象都可能有多个属性(attribute)，属性可能来自于其类定义或是继承类定义，叫做类属性(class attribute)，也可能是该对象实例定义的，叫做对象属性(object attribute)。对象的属性储存在对象的\_\_dict\_\_属性中。\_\_dict\_\_为一个词典，键为属性名，对应的值为属性本身。

Python中的属性是分层定义的，当我们需要调用某个属性的时候，Python会一层层向上遍历，直到找到那个属性。(某个属性可能出现再不同的层被重复定义，Python向上的过程中，会选取先遇到的那一个，也就是比较低层的属性定义)。

特性（property）是特殊的属性，该属性对其他属性有依赖关系，特性使用内置函数property()来创建。property()最多可以加载四个参数。前三个参数为函数，分别用于处理查询特性、修改特性、删除特性。最后一个参数为特性的文档，可以为一个字符串，起说明作用。

```python
class num(object):
    def __init__(self, value):
        self.value = value
    def getNeg(self):
        return -self.value
    def setNeg(self, value):
        self.value = -value
    def delNeg(self):
        print("value also deleted")
        del self.value
    neg = property(getNeg, setNeg, delNeg, "I'm negative")

x = num(1.1)
print(x.neg)
x.neg = -22
print(x.value)
print(num.neg.__doc__)
del x.neg
```

使用特殊方法\_\_getattr\_\_(self, name)来查询即时生成的属性，使用\_\_getattribute\_\_特殊方法用于查询任意属性。

***

## 闭包（closure）

闭包是一个包含有环境变量取值的函数对象，环境变量取值被保存在函数对象的\_\_closure\_\_属性中。

```python
def line_conf(a, b):
    def line(x):
        return ax + b
    return line

line1 = line_conf(1, 1)
line2 = line_conf(4, 5)
print(line1(5), line2(5))
```

函数line与环境变量a,b构成闭包。在创建闭包的时候通过line_conf的参数a,b说明了这两个环境变量的取值，这样，就确定了函数的最终形式(y = x + 1和y = 4x + 5)

***

## 装饰器

装饰器可以对一个函数、方法或者类进行加工

