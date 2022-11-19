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

### all()

{% tabs 函数 %}
<!-- tab 描述 -->
all() 函数用于判断给定的可迭代参数 iterable 中的所有元素是否都为 TRUE，如果是返回 True，否则返回 False。

元素除了是 0、空、None、False 外都算 True。

函数等价于：
```python
def all(iterable):
    for element in iterable:
        if not element:
            return False
    return True
```
<!-- endtab -->
<!-- tab 语法 -->
```python
all(iterable)
```
<!-- endtab -->
<!-- tab 参数 -->
* iterable -- 元组或列表。
<!-- endtab -->
<!-- tab 返回值 -->
如果iterable的所有元素不为0、''、False或者iterable为空，all(iterable)返回True，否则返回False；

**注意**：空元组、空列表返回值为True，这里要特别注意。
<!-- endtab -->
<!-- tab 实例 -->
```python
>>> all(['a', 'b', 'c', 'd'])  # 列表list，元素都不为空或0
True
>>> all(['a', 'b', '', 'd'])   # 列表list，存在一个为空的元素
False
>>> all([0, 1，2, 3])          # 列表list，存在一个为0的元素
False
   
>>> all(('a', 'b', 'c', 'd'))  # 元组tuple，元素都不为空或0
True
>>> all(('a', 'b', '', 'd'))   # 元组tuple，存在一个为空的元素
False
>>> all((0, 1, 2, 3))          # 元组tuple，存在一个为0的元素
False
   
>>> all([])             # 空列表
True
>>> all(())             # 空元组
True
```
<!-- endtab -->
{% endtabs %}

### int()

{% tabs 函数 %}
<!-- tab 描述 -->
int() 函数用于将一个字符串或数字转换为整型。
<!-- endtab -->
<!-- tab 语法 -->
```python
class int(x, base=10)
```
<!-- endtab -->
<!-- tab 参数 -->
* x -- 字符串或数字。
* base -- 进制数，默认十进制。
<!-- endtab -->
<!-- tab 返回值 -->
返回整型数据。
<!-- endtab -->
<!-- tab 实例 -->
```python
>>>int()               # 不传入参数时，得到结果0
0
>>> int(3)
3
>>> int(3.6)
3
>>> int('12',16)        # 如果是带参数base的话，12要以字符串的形式进行输入，12 为 16进制
18
>>> int('0xa',16)  
10  
>>> int('10',8)  
8
```
<!-- endtab -->
{% endtabs %}


### ord()

{% tabs 函数 %}
<!-- tab 描述 -->
ord() 函数是 chr() 函数（对于8位的ASCII字符串）或 unichr() 函数（对于Unicode对象）的配对函数，它以一个字符（长度为1的字符串）作为参数，返回对应的 ASCII 数值，或者 Unicode 数值，如果所给的 Unicode 字符超出了你的 Python 定义范围，则会引发一个 TypeError 的异常。
<!-- endtab -->
<!-- tab 语法 -->
```python
ord(c)
```
<!-- endtab -->
<!-- tab 参数 -->
* c -- 字符。
<!-- endtab -->
<!-- tab 返回值 -->
返回值是对应的十进制整数。
<!-- endtab -->
<!-- tab 实例 -->
```python
>>>ord('a')
97
>>> ord('b')
98
>>> ord('c')
99
```
<!-- endtab -->
{% endtabs %}

### str()

{% tabs 函数 %}
<!-- tab 描述 -->
str() 函数将对象转化为适于人阅读的形式。
<!-- endtab -->
<!-- tab 语法 -->
```python
class str(object='')
```
<!-- endtab -->
<!-- tab 参数 -->
* object -- 对象。
<!-- endtab -->
<!-- tab 返回值 -->
返回一个对象的string格式。
<!-- endtab -->
<!-- tab 实例 -->
```python
>>>s = 'RUNOOB'
>>> str(s)
'RUNOOB'
>>> dict = {'runoob': 'runoob.com', 'google': 'google.com'};
>>> str(dict)
"{'google': 'google.com', 'runoob': 'runoob.com'}"
```
<!-- endtab -->
{% endtabs %}

### any()

{% tabs 函数 %}
<!-- tab 描述 -->
any() 函数用于判断给定的可迭代参数 iterable 是否全部为 False，则返回 False，如果有一个为 True，则返回 True。

元素除了是 0、空、FALSE 外都算 TRUE。

函数等价于：
```python
def any(iterable):
    for element in iterable:
        if element:
            return True
    return False
```
<!-- endtab -->
<!-- tab 语法 -->
```python
any(iterable)
```
<!-- endtab -->
<!-- tab 参数 -->
* iterable -- 元组或列表。
<!-- endtab -->
<!-- tab 返回值 -->
如果都为空、0、false，则返回false，如果不都为空、0、false，则返回true。
<!-- endtab -->
<!-- tab 实例 -->
```python
>>>any(['a', 'b', 'c', 'd'])  # 列表list，元素都不为空或0
True
 
>>> any(['a', 'b', '', 'd'])   # 列表list，存在一个为空的元素
True
 
>>> any([0, '', False])        # 列表list,元素全为0,'',false
False
 
>>> any(('a', 'b', 'c', 'd'))  # 元组tuple，元素都不为空或0
True
 
>>> any(('a', 'b', '', 'd'))   # 元组tuple，存在一个为空的元素
True
 
>>> any((0, '', False))        # 元组tuple，元素全为0,'',false
False
  
>>> any([]) # 空列表
False
 
>>> any(()) # 空元组
False
```
<!-- endtab -->
{% endtabs %}

### eval()

{% tabs 函数 %}
<!-- tab 描述 -->
eval() 函数用来执行一个字符串表达式，并返回表达式的值。
<!-- endtab -->
<!-- tab 语法 -->
```python
eval(expression[, globals[, locals]])
```
<!-- endtab -->
<!-- tab 参数 -->
* expression -- 表达式。
* globals -- 变量作用域，全局命名空间，如果被提供，则必须是一个字典对象。
* locals -- 变量作用域，局部命名空间，如果被提供，可以是任何映射对象。
<!-- endtab -->
<!-- tab 返回值 -->
返回表达式计算结果。
<!-- endtab -->
<!-- tab 实例 -->
```python
>>>x = 7
>>> eval( '3 * x' )
21
>>> eval('pow(2,2)')
4
>>> eval('2 + 2')
4
>>> n=81
>>> eval("n + 4")
85
```
<!-- endtab -->
{% endtabs %}

### isinstance()

{% tabs 函数 %}
<!-- tab 描述 -->
isinstance() 函数来判断一个对象是否是一个已知的类型，类似 type()。
{% tip bell %}
isinstance() 与 type() 区别：

type() 不会认为子类是一种父类类型，不考虑继承关系。

isinstance() 会认为子类是一种父类类型，考虑继承关系。

如果要判断两个类型是否相同推荐使用 isinstance()。
{% endtip %}
<!-- endtab -->
<!-- tab 语法 -->
```python
isinstance(object, classinfo)
```
<!-- endtab -->
<!-- tab 参数 -->
* object -- 实例对象。
* classinfo -- 可以是直接或间接类名、基本类型或者由它们组成的元组。
<!-- endtab -->
<!-- tab 返回值 -->
如果对象的类型与参数二的类型（classinfo）相同则返回 True，否则返回 False。
<!-- endtab -->
<!-- tab 实例 -->
```python
>>>a = 2
>>> isinstance (a,int)
True
>>> isinstance (a,str)
False
>>> isinstance (a,(str,int,list))    # 是元组中的一个返回 True
True
```
{% span h4 red ,type() 与 isinstance()区别： %}
```python
class A:
    pass
 
class B(A):
    pass
 
isinstance(A(), A)    # returns True
type(A()) == A        # returns True
isinstance(B(), A)    # returns True
type(B()) == A        # returns False
```
<!-- endtab -->
{% endtabs %}

### pow()

{% tabs 函数 %}
<!-- tab 描述 -->
pow() 方法返回 x^y（x 的 y 次方） 的值。
<!-- endtab -->
<!-- tab 语法 -->
以下是 math 模块 pow() 方法的语法:
```python
import math
math.pow( x, y )
```
内置的 pow() 方法: 
```python
pow(x, y[, z])
```
函数是计算 x 的 y 次方，如果 z 在存在，则再对结果进行取模，其结果等效于 pow(x,y) %z。

**注意**：pow() 通过内置的方法直接调用，内置方法会把参数作为整型，而 math 模块则会把参数转换为 float。
<!-- endtab -->
<!-- tab 参数 -->
* x -- 数值表达式。
* y -- 数值表达式。
* z -- 数值表达式。
<!-- endtab -->
<!-- tab 返回值 -->
返回 x^y（x的y次方） 的值。
<!-- endtab -->
<!-- tab 实例 -->
```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
 
import math   # 导入 math 模块
 
print "math.pow(100, 2) : ", math.pow(100, 2)
# 使用内置，查看输出结果区别
print "pow(100, 2) : ", pow(100, 2)
 
print "math.pow(100, -2) : ", math.pow(100, -2)
print "math.pow(2, 4) : ", math.pow(2, 4)
print "math.pow(3, 0) : ", math.pow(3, 0)
```
以上实例运行后输出结果为：
```python
math.pow(100, 2) :  10000.0
pow(100, 2) :  10000
math.pow(100, -2) :  0.0001
math.pow(2, 4) :  16.0
math.pow(3, 0) :  1.0
```
<!-- endtab -->
{% endtabs %}