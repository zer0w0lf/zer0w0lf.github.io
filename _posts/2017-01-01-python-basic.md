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
# 变量不需要事先声明，在赋值时自动确定类型
a = 10

# 查看变量的类型使用type函数
print(type(a))
```

### 基本数据类型

```python
a = 10         # int 整数
a = 1.3        # float 浮点数
a = True       # 真值 (True/False)
a = 'Hello!'   # 字符串。字符串也可以用双引号。
```

### 序列(sequence)

序列是有顺序的对象元素的集合，可以没有对象元素或包含一个或多个对象元素，序列有元组和列表两种。

- 元组(tuple)：也称为定值表，对象元素以()包含，一旦建立，各个对象元素不可再变更
- 列表(list): 对象元素以[]包含，各个对象元素可以再变更

```python
s1 = (2, 1.3, 'love', 5.6, 9, 12, False)         # s1是一个tuple
s2 = [True, 5, 'smile']                          # s2是一个list
```

序列中单个元素对象引用：序列的引用通过s[<int\>]实现，int为下标，下标从0开始

```python
print(s1[0])
```

序列的范围引用：基本样式[下限:上限:步长]。范围引用时如果写明上限，那么这个上限本身不包括在内

```python
print(s1[:5])             # 从开始到下标4 （下标5的元素 不包括在内）
print(s1[2:])             # 从下标2到最后
print(s1[0:5:2])          # 从下标0到下标4 (下标5不包括在内)，每隔2取一个元素 （下标为0，2，4的元素）
print(s1[2:0:-1])         # 从下标2到下标1
#尾部元素引用
print(s1[-1])             # 序列最后一个元素
print(s1[-3])             # 序列倒数第三个元素
```

### 词典(dictionary)

词典是包含有多个元素，每个元素包含键和值两部分，每个元素以逗号分隔。以不可变的对象作为键，如以字符串、数字或者真值来表示键，值可以是任意对象。键和值两者一一对应

```python
dic = {'tom':11, 'sam':57, 'lily':100}
```

词典的元素没有顺序，不能通过下标引用元素，词典是通过键来引用

```python
print dic['tom']
dic['tom'] = 30    #修改词典元素
dic['lilei'] = 99  #词典中增添一个新元素
print dic
```

### 动态类型

Python的变量(variable)不需要声明，而在赋值时，变量可以重新赋值为任意值。动态类型的核心是对象和引用分离，对象是存储在内存中的实体，对象名是指向对象的引用。

```python
a = 3        # 3是储存在内存中的一个整数对象。通过赋值，引用a指向对象3
a = 'at'     # 内存中建立对象‘at’，是一个字符串(string)。引用a指向了'at'
a = 5    
b = a        # 让引用b指向引用a所指的那一个对象
a = a + 2    # 对引用a重新赋值，让a指向一个新的对象7
```

- 可变数据对象(mutable object)，可以通过引用其元素，改变对象自身(in-place change)，如列表和词典

- 不可变数据对象(immutable object)，不能改变对象本身，只能改变引用的指向，如数字、字符串和元组

***

## 运算

数学运算

```python
print 1+9        # 加法
print 1.3-4      # 减法
print 3*5        # 乘法
print 4.5/1.5    # 除法
print 3**2       # 乘方     
print 10%3       # 求余数
```

判断：判断是真还是假，返回True/False

```python
print 5==6               # ==， 相等
print 8.0!=8.0           # !=, 不等
print 3<3, 3<=3          # <, 小于; <=, 小于等于
print 4>5, 4>=0          # >, 大于; >=, 大于等于
print 5 in [1,3,5]       # 5是list [1,3,5]的一个元素
```

逻辑运算：True/False之间的运算

```python
print True and True, True and False      # and, “与”运算， 两者都为真才是真
print True or False                      # or, "或"运算， 其中之一为真即为真
print not True                           # not, “非”运算， 取反
```

***

## 条件与循环

### if条件语句

以四个空格的缩进来表示隶属关系, Python中不能随意缩进

```python
if  <条件1>:
    statement
elif <条件2>:
    statement
elif <条件3>:
    statement
else:
    statement
```

### for循环

需要预先设定好循环的次数(n)，然后执行隶属于for的语句n次

```python
for element in sequence:   # 每次从sequence中取出一个元素赋值给element，然后执行statement
    statement

dic = {'lilei': 90, 'lily': 100, 'sam': 57, 'tom': 90}
for key in dic:       # 词典元素的循环调用，dict的每个键，被提取出来，赋予给key变量
    print dic[key]
```

利用enumerate()函数，可以在每次循环中同时得到下标和元素，返回的是一个包含两个元素的定值表(tuple)，两个元素分别赋予index和char

```python
S = 'abcdefghijk'
for (index,char) in enumerate(S):
    print index
    print char
```

zip()函数从多个列表中，依次各取出一个元素。合并成的元组放入zip()返回的列表中。每次循环时，从各个序列分别从左到右取出一个元素，合并成一个tuple，然后tuple的元素赋予给a,b,c

```python
ta = [1, 2, 3]
tb = [9, 8, 7]
tc = ['a', 'b', 'c']
for (a, b, c) in zip(ta, tb, tc):
    print(a, b, c)
```

### while循环

不停地循环执行隶属于它的语句，直到条件为假(False)

```python
while condition:
    statement
```

### 中断循环

```python
continue   # 在循环的某一次执行中，如果遇到continue, 那么跳过这一次执行，进行下一次的操作
break      # 停止执行整个循环
```

### 循环对象

open()返回的实际上是一个循环对象，包含有next()方法，当一个循环结构（比如for）调用循环对象时，它就会每次循环的时候调用next()方法，直到StopIteration出现

```python
for line in open('test.txt'):
    print line
```

### 生成器(generator)

构成一个用户自定义的循环对象。生成器的编写方法和函数定义类似，只是在return的地方改为yield。生成器中可以有多个yield。当生成器遇到一个yield时，会暂停运行生成器，返回yield后面的值。当再次调用生成器的时候，会从刚才暂停的地方继续运行，直到下一个yield

```python
def gen():
    a = 100
    yield a
    a = a*8
    yield a
    yield 1000
```

生成器表达式(Generator Expression)：G = (x for x in range(4))

### 表推导(list comprehension)

快速生成表的方法

```python
L = [x**2 for x in range(10)]
```

***

## 函数及调用

### 函数定义

```python
def function_name(para1, para2, para3):  # 函数参数不是必须的
    statement
    return something  
```

return并不是必须的，当没有return, 或者return后面没有返回值时，函数将自动返回None。return可以返回多个值，以逗号分隔，如return a,b,c，相当于返回一个tuple(定值表)

### 函数调用

函数的参数传递，本质上传递的是引用。

基本数据类型的参数通过值传递，不影响原来的变量。

```python
a = 1

def change_integer(a):
    a = a + 1
    return a

print change_integer(a)
print a   # a的值为1，保持不变
```

表类型的参数通过指针传递，影响原来的变量

```python
b = [1,2,3]

def change_list(b):
    b[0] = b[0] + 1
    return b

print change_list(b)
print b    # 列表b的值发生变化
```

关键字传递：根据每个参数的名字传递参数，关键字并不用遵守位置的对应关系

```python
def f(a,b,c):
    return a+b+c

print(f(c=3,b=2,a=1))
```

参数默认值：定义函数时，可以给参数富裕默认值；调用时若没有传值，则使用默认值

```python
def f(a,b,c=10):
    return a+b+c

print(f(3,2))
print(f(3,2,1))
```

包裹传递：定义函数时，并不知道调用时会传递多少参数的情况，使用包裹传递

包裹位置参数：

```python
def func(*name):  # 所有的参数被name收集，根据位置合并成一个元组(tuple)，name是包裹位置传递所用的元组名，在定义func时，在name前加*号
    print type(name)
    print name

func(1,4,6)
func(5,6,7,1,2,3)
```

包裹关键字参数：

```python
def func(**dict):  # dict是一个字典，收集所有的关键字，传递给函数func。参数dict是包裹关键字传递所用的字典，在dict前加**
    print type(dict)
    print dict

func(a=1,b=9)
func(m=2,n=1,c=11)
```

解包裹：调用时，使用*或**解包裹

```python
def func(a,b,c):
    print a,b,c

args = (1,3,4)
func(*args)   # 在传递tuple时，让tuple的每一个元素对应一个位置参数

dict = {'a':1,'b':2,'c':3}
func(**dict)  # 在传递词典dict时，让词典的每个键值对作为一个关键字传递给func
```

混合传递：基本原则是，先位置，再关键字，再包裹位置，再包裹关键字

### 内置函数

```python
# 内置函数dir()：用来查询一个类或者对象所有属性
print dir(list)

# 内置函数help()：用来查询的说明文档
print help(list)

# 词典对象常用方法
print dic.keys()           # 返回dic所有的键
print dic.values()         # 返回dic所有的值
print dic.items()          # 返回dic所有的元素（键值对）
dic.clear()                # 清空dic，dict变为{}
del dic['tom']             # 删除 dic 的‘tom’元素，del是Python中保留的关键字，用于删除对象。
print(len(dic))            # 可以用len()查询词典中的元素总数
```

### 函数对象

函数对象具有属性、赋值给其他对象名，或作为参数传递

```python
# lambda生成一个函数对象

func = lambda x,y: x + y
print func(3,4)

# 函数可以作为一个对象，进行参数传递

def test(f, a, b):
    print 'test'
    print f(a, b)

test(func, 3, 5)
```

map()为python内置函数，第一个参数为函数对象，功能是将函数对象依次作用于表的每一个元素，每次作用的结果储存于返回的表中。在Python 3.X中，map()的返回值是一个循环对象。可以利用list()函数，将该循环对象转换成表

```python
re = map((lambda x,y: x+y),[1,2,3],[6,7,9])
```

filter函数的第一个参数也是一个函数对象。它也是将作为参数的函数对象作用于多个元素。如果函数对象返回的是True，则该次的元素被储存于返回的表中。filter通过读入的函数来筛选数据。同样，在Python 3.X中，filter返回的不是表，而是循环对象

```python
def func(a):
    if a > 100:
        return True
    else:
        return False

print filter(func,[10,56,101,500])
```

reduce函数的第一个参数也是函数，但有一个要求，就是这个函数自身能接收两个参数。reduce可以累进地将函数作用于各个参数

```python
print reduce((lambda x,y: x+y),[1,2,5,7,9])

# reduce将表中的前两个元素(1和2)传递给lambda函数，得到3。该返回值(3)将作为lambda函数的第一个参数，而表中的下一个元素(5)作为lambda函数的第二个参数，进行下一次的对lambda函数的调用，得到8
```

***

## 类（class）

### 类的定义

```python
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
```

### 创建对象

```python
objectname = Classname()
```

### 引用对象的属性

```python
objectname.attribute

#list是一个类
nl = [1,2,5,3,5]        # nl是类list的一个对象。
print nl.count(5)       # 计数，看总共有多少个5
print nl.index(3)       # 查询 nl 的第一个3的下标
nl.append(6)            # 在 nl 的最后增添一个新元素6
nl.sort()               # 对nl的元素排序
print nl.pop()          # 从nl中去除最后一个元素，并将该元素返回。
nl.remove(2)            # 从nl中去除第一个2
nl.insert(0,9)          # 在下标为0的位置插入9
```

说明：

- name：当name为“object”时，表示该类没有父类；当name为父类名称时，则定义的为父类的子类，即子类继承父类(inheritance)，子类继承父类的所有属性和方法
- self：类中定义的方法第一个参数必须为self，代表了根据类定义而创建的对象，可以通过self调用类的属性和方法。**可以通过对象修改类的属性值，但这很危险，类属性值的改变会影响类的所有对象**
- 特殊方法：以“\_\_”开头的方法为特殊方法(special method)，\_\_init\_\_()特殊方法在创建对象时会自动调用该方法，此过程也叫初始化。运算符+、-、*等是特殊方法

## 模块

一个.py文件就是一个模块，通过import模块的方式来调用对应模块的对象

```python
import a                  # 引入模块a，使用a中的对象时需要使用a.
import a as b             # 引入模块a，并将模块a重命名为b
from a import function1   # 从模块a中引入function1对象。调用a中对象时，我们不用再说明模块，即直接使用function1，而不是a.function1。
from a import *           # 从模块a中引入所有对象。调用a中对象时，我们不用再说明模块，即直接使用对象，而不是a.对象。
```
python会在以下路径中搜索它想要寻找的模块：

- 程序所在的文件夹
- 标准库的安装路径
- 操作系统环境变量PYTHONPATH所包含的路径

模块包：可以将功能相似的模块放在同一文件夹中，构成模块包。模块包文件夹中必须包含一个\_\_init\_\_.py的文件，提醒Python，该文件夹为一个模块包。\_\_init\_\_.py可以是一个空文件

```python
import this_dir.module  # 引入this_dir文件夹中的module模块
```

## 文本文件的输入输出

创建文件对象：

```python
f = open(文件名，模式) 
```

打开一个文件，并使用一个对象来表示该文件，最常用的模式有，"r"（只读），“w”（写入）

```python
f = open("test.txt","r")
```

```python
# 文件对象的方法
content = f.read(N)          # 读取N bytes的数据
content = f.readline()       # 读取一行
content = f.readlines()      # 读取所有行，储存在列表中，每个元素是一行。

f.write('I like apple')      # 将'I like apple'写入文件

f.close()                    # 关闭文件
```

## 异常处理

异常处理完整语法结构：

```python
try:
    ...
except exception1:
    ...
except exception2:
    ...
except:
    ...
else:
    ...
finally:
    ...
```

如果try中有异常发生时，将执行异常的归属，执行except。异常层层比较，看是否是exception1, exception2...，直到找到其归属，执行相应的except中的语句。如果except后面没有任何参数，那么表示所有的exception都交给这段程序处理。如果try中没有异常，那么except部分将跳过，执行else中的语句。finally是无论是否有异常，最后都要做的一些事情。

整个流程如下：

- try\-\>异常\-\>except\-\>finally
- try\-\>无异常\-\>else\-\>finally

抛出异常：使用raise exception

```python
print 'Lalala'
raise StopIteration
print 'Hahaha
```
