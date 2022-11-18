---
title: Python语法
date: 2022-11-18 23:45:07
updated: 2022-11-19 00:40:20
tag:
  - python
  - 语法
---

{% note flat info %}均基于Python3.x{% endnote %}

{% folding red ,常用格式 %}
```
{% tabs 函数 %}
<!-- tab 描述 -->

<!-- endtab -->
<!-- tab 语法 -->

<!-- endtab -->
<!-- tab 参数 -->

<!-- endtab -->
<!-- tab 返回值 -->

<!-- endtab -->
<!-- tab 实例 -->

<!-- endtab -->
{% endtabs %}
```
{% endfolding %}

## 1. 内置函数

### emunerate()

{% tabs 函数 %}
<!-- tab 描述 -->
enumerate() 函数用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时**列出数据**和**数据下标**，一般用在 for 循环当中。
<!-- endtab -->
<!-- tab 语法 -->
```python
enumerate(sequence, [start=0])
```
<!-- endtab -->
<!-- tab 参数 -->
* sequence -- 一个序列、迭代器或其他支持迭代对象。
* start -- 下标起始位置的值。
<!-- endtab -->
<!-- tab 返回值 -->
返回 enumerate(枚举) 对象。
<!-- endtab -->
<!-- tab 实例 -->
```python
>>> seq = ['one', 'two', 'three']
>>> for i, element in enumerate(seq):
...     print i, element
...
0 one
1 two
2 three
```
<!-- endtab -->
{% endtabs %}

### dict()

{% tabs 函数 %}
<!-- tab 描述 -->
dict() 函数用于创建一个字典。
<!-- endtab -->
<!-- tab 语法 -->
```python
class dict(**kwarg)
class dict(mapping, **kwarg)
class dict(iterable, **kwarg)
```
<!-- endtab -->
<!-- tab 参数 -->
* **kwargs -- 关键字。
* mapping -- 元素的容器，映射类型（Mapping Types）是一种关联式的容器类型，它存储了对象与对象之间的映射关系。
* iterable -- 可迭代对象。
<!-- endtab -->
<!-- tab 返回值 -->
返回一个字典。
<!-- endtab -->
<!-- tab 实例 -->
```python
>>>dict()                        # 创建空字典
{}
>>> dict(a='a', b='b', t='t')     # 传入关键字
{'a': 'a', 'b': 'b', 't': 't'}
>>> dict(zip(['one', 'two', 'three'], [1, 2, 3]))   # 映射函数方式来构造字典
{'three': 3, 'two': 2, 'one': 1} 
>>> dict([('one', 1), ('two', 2), ('three', 3)])    # 可迭代对象方式来构造字典
{'three': 3, 'two': 2, 'one': 1}
```
<!-- endtab -->
{% endtabs %}

### abs()

{% tabs 函数 %}
<!-- tab 描述 -->
abs() 函数返回数字的绝对值。
<!-- endtab -->
<!-- tab 语法 -->
```python
abs( x )
```
<!-- endtab -->
<!-- tab 参数 -->
* x -- 数值表达式。
<!-- endtab -->
<!-- tab 返回值 -->
函数返回x（数字）的绝对值。
<!-- endtab -->
<!-- tab 实例 -->
输入：
```python
#!/usr/bin/python
 
print "abs(-45) : ", abs(-45)
print "abs(100.12) : ", abs(100.12)
print "abs(119L) : ", abs(119L)
```
输出：
```python
abs(-45) :  45
abs(100.12) :  100.12
abs(119L) :  119
```
<!-- endtab -->
{% endtabs %}

### divmod()

{% tabs 函数 %}
<!-- tab 描述 -->
python divmod() 函数把除数和余数运算结果结合起来，返回一个包含商和余数的元组(a // b, a % b)。
<!-- endtab -->
<!-- tab 语法 -->
```python
divmod(a, b)
```
<!-- endtab -->
<!-- tab 参数 -->
* a: 数字
* b: 数字
<!-- endtab -->
<!-- tab 实例 -->
```python
>>>divmod(7, 2)
(3, 1)
>>> divmod(8, 2)
(4, 0)
>>> divmod(1+2j,1+0.5j)
((1+0j), 1.5j)
```
<!-- endtab -->
{% endtabs %}

### input()

{% tabs 函数 %}
<!-- tab 描述 -->
input() 函数接受一个标准输入数据，返回为 string 类型。
<!-- endtab -->
<!-- tab 语法 -->
```python
input([prompt])
```
<!-- endtab -->
<!-- tab 参数 -->
* prompt: 提示信息
<!-- endtab -->
<!-- tab 实例 -->
```python
>>>a = input("input:")
input:123                  # 输入整数
>>> type(a)
<class 'str'>              # 字符串
>>> a = input("input:")    
input:runoob              # 正确，字符串表达式
>>> type(a)
<class 'str'>             # 字符串
```
<!-- endtab -->
{% endtabs %}

### open()

{% tabs 函数 %}
<!-- tab 描述 -->
open() 函数用于打开一个文件，创建一个 file 对象，相关的方法才可以调用它进行读写。
<!-- endtab -->
<!-- tab 语法 -->
```python
open(name[, mode[, buffering]])
```
<!-- endtab -->
<!-- tab 参数 -->
* name : 一个包含了你要访问的文件名称的字符串值。

* mode : mode 决定了打开文件的模式：只读，写入，追加等。所有可取值见如下的完全列表。这个参数是非强制的，默认文件访问模式为只读(r)。

* buffering : 如果 buffering 的值被设为 0，就不会有寄存。如果 buffering 的值取 1，访问文件时会寄存行。如果将 buffering 的值设为大于 1 的整数，表明了这就是的寄存区的缓冲大小。如果取负值，寄存区的缓冲大小则为系统默认。

不同模式打开文件的完全列表：

|模式|描述|
|-------|----|
|t	|文本模式 (默认)。|
|x	|写模式，新建一个文件，如果该文件已存在则会报错。|
|b	|二进制模式。|
|+	|打开一个文件进行更新(可读可写)。|
|U	|通用换行模式（不推荐）。|
|r	|以只读方式打开文件。文件的指针将会放在文件的开头。这是默认模式。|
|rb	|以二进制格式打开一个文件用于只读。文件指针将会放在文件的开头。这是默认模式。一般用于非文本文件如图片等。|
|r+	|打开一个文件用于读写。文件指针将会放在文件的开头。|
|rb+|	以二进制格式打开一个文件用于读写。文件指针将会放在文件的开头。一般用于非文本文件如图片等。|
|w	|打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。|
|wb	|以二进制格式打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。|
|w+	|打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。|
|wb+|	以二进制格式打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。一般用于非文本文件如图片等。|
|a	|打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。|
|ab	|以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。|
|a+	|打开一个文件用于读写。如果该文件已存在，文件指针将会放在文件的结尾。文件打开时会是追加模式。如果该文件不存在，创建新文件用于读写。|
|ab+	|以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。如果该文件不存在，创建新文件用于读写。|
<!-- endtab -->
{% endtabs %}

### staticmethod()

{% tabs 函数 %}
<!-- tab 描述 -->
staticmethod 返回函数的静态方法。

该方法不强制要求传递参数，如下声明一个静态方法：
```python
class C(object):
    @staticmethod
    def f(arg1, arg2, ...):
        ...
```
以上实例声明了静态方法 f，从而可以实现实例化使用 C().f()，当然也可以不实例化调用该方法 C.f()。
<!-- endtab -->
<!-- tab 语法 -->
```python
staticmethod(function)
```
<!-- endtab -->
<!-- tab 实例 -->
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
class C(object):
    @staticmethod
    def f():
        print('runoob');
 
C.f();          # 静态方法无需实例化
cobj = C()
cobj.f()        # 也可以实例化后调用
```
以上实例输出结果为：
```python
runoob
runoob
```
<!-- endtab -->
{% endtabs %}
