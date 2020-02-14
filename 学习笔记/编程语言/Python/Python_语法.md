# 如何使用本篇笔记？

- 简要记录基本的语法



**规范**

- 三层标题
- 小标题用黑体字
- 代码用代码块表示



[TOC]

# 简介

Python是一种解释型、面向对象、动态数据类型的高级程序设计语言。

Python 是一个高层次的结合了解释性、编译性、互动性和面向对象的脚本语言。 

Python 的设计具有很强的可读性，相比其他语言经常使用英文关键字，其他语言的一些标点符号，它具有比其他语言更有特色语法结构。

- Python 是一种解释型语言： 这意味着开发过程中没有了编译这个环节。类似于PHP和Perl语言。
- Python 是交互式语言： 这意味着，您可以在一个 Python 提示符 >>> 后直接执行代码。
- Python 是面向对象语言: 这意味着Python支持面向对象的风格或代码封装在对象的编程技术。
- Python 是初学者的语言：Python 对初级程序员而言，是一种伟大的语言，它支持广泛的应用程序开发，从简单的文字处理到 WWW 浏览器再到游戏。

## 历史

Python由Guido van Rossum于1989年底发明，第一个公开发行版发行于1991年。Python源代码遵循GPL(GUN General Public License) 协议。（在八十年代末和九十年代初，在荷兰国家数学和计算机科学研究所设计出来的）

Python2.0于2000年10月16日发布，增加了实现完整的垃圾回收，并且支持Unicode

Python 3.0 于 2008 年 12 月 3 日发布，此版不完全兼容之前的 Python 源代码。不过，很多新特性后来也被移植到旧的Python 2.6/2.7版本

Python2.7被确定为最后一个Python2.x版本

Python3.0版本，常被称为Python3000，或简称Py3k。相当于Python的早期版本，这是一个较大的升级。Python3.0在设计的时候没有考虑向下兼容

官方宣布，2020 年 1 月 1 日， 停止 Python 2 的更新。

## 运行环境

安装Python3

配置环境变量



## 开发环境

vim emacs sublime

PyCharm

Eclipse with Pydev

Komodo Edit

Wing

PyScripter

The Eric Python IDE

Interactive Editor for Python

[官网收集的Python IDE](https://wiki.python.org/moin/PythonEditors)

# 基础语法

[Python入门指南](https://docs.python.org/3/tutorial/appetite.html)      [Python入门指南 中文手册](https://www.runoob.com/manual/pythontutorial3/docs/html/)

## 命令行

命令行解释



脚本文件

```python
#!/usr/bin/python3
# -*- coding: utf-8 -*-  指定编码
print("Hello World!")
```
```bash
$ python3 hello.py #执行脚本
```

命令行参数

```bash
$ python3


-d #在解析时显示调试信息
-O #生成优化代码(.pyo文件)
-S #启动时不引入查找Python路径的位置
-V #输出Python版本号
-X #已过时
-c cmd #执行Python脚本，并将运行结果作为cmd字符串
file #执行给定文件
```

[命令行参数](https://www.runoob.com/python3/python3-command-line-arguments.html)

## 规则

**标识符**

- 区分大小写
- 第一个字符是字母表中的字母或下划线_
- 其他部分字符是由字母、数字和下划线组成

**保留字**

```bash
# 保留字即是关键字，不能与标识符起冲突
# Python标准库提供了一个keyword模块,可以输出当前版本的所有关键字
>>> import keyword
>>> keyword.kwlist
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

**缩进**

Python用缩进来表示代码块，不需要使用大括号{}

缩进的空格数是可变的，但是同一个代码块的语句必须包含相同的缩进空格数

**多行语句**

```python
# Python语句如果很长，可以用反斜杠来实现多行语句
total = item_one + \
        item_two + \
        item_three

# 在(),[],{}中的多行语句，不需要使用反斜杠
total = ['item_one', 'item_two', 'item_three',
        'item_four', 'item_five']
```

**注释**

```python
# Python中单行注释以#开头

'''
多行注释可以用''' '''和"""  """
'''
```



**编程规范**

[编码规范](https://www.runoob.com/w3cnote/google-python-styleguide.html)



## 数据类型

### Number 数字

int整数

bool布尔值

float浮点数

complex复数

### String 字符串

### List 列表

### Tuple 元组

### Set 集合

### Dictionary 字典

### 数据类型转换

## 运算符



## 语句

```python
# Python可以在同一行中使用多条语句，语句之间使用分号(;)分割

#!/usr/bin/python3 
import sys; x = 'runoob'; sys.stdout.write(x + '\n')

# 缩进相同的一组语句构成一个代码块，我们称之代码组
# 像if、while、def和class这样的复合语句，首行以关键字开始，以冒号( : )结束，该行之后的一行或多行代码构成代码组。我们将首行及后面的代码组称为一个子句(clause)

```



### 条件语句

### 循环语句

### 迭代器与生成器



## 函数

函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。

空行与代码缩进不同，空行并不是Python语法的一部分。书写时不插入空行，Python解释器运行也不会出错。但是空行的作用在于分隔两段不同功能或含义的代码，便于日后代码的维护或重构。

记住：空行也是程序代码的一部分。

### 函数

### 参数

### 返回值



### 内置函数

```python
# print默认输出是换行的，如果要实现不换行需要在变量末尾加上 end=""：

#!/usr/bin/python3 
x="a"
y="b"
# 换行输出
print( x )
print( y )

print('---------')
# 不换行输出
print( x, end=" " )
print( y, end=" " )
print()

输出为：
a
b
---------
a b
```





## 模块

import

from import

在 python 用 **import** 或者 **from...import** 来导入相应的模块。

将整个模块(somemodule)导入，格式为： **import somemodule**

从某个模块中导入某个函数,格式为： **from somemodule import somefunction**

从某个模块中导入多个函数,格式为： **from somemodule import firstfunc, secondfunc, thirdfunc**

将某个模块中的全部函数导入，格式为： **from somemodule import \***

```python
# 导入sys模块
import sys
# 导入sys模块的argv,path成员
from sys import argv,path
```







## 作用域





# 面向对象



### 多态

### 封装

### 异常

### 迭代器













# 标准库

# 第三方模块





**常用模块有这些**

文件io

File

os文件

正则表达式

http原理

MySQL

网络编程

SMTP

多线程

XML解析

GUI编程

JSON









# 其他







# 参考书目

《Python基础教程》[挪]海特兰德 著 人民邮电出版社 ISBN 978-7115353528

[随书源码第二版](https://www.apress.com/cn/book/9781590599822)

[随书源码第三版](https://www.apress.com/cn/book/9781484200292)

[随书源码第三版Github地址](https://github.com/apress/beginning-python-3ed)



# 链接

[Python官网主页](https://www.python.org/) 

[Scrapy | A Fast and Powerful Scraping and Web Crawling Framework](https://scrapy.org/) 

[python -m pip install xxx](http://www.runoob.com/w3cnote/python-pip-install-usage.html) 

[爬虫 - 标签 - python修行路 - 博客园](https://www.cnblogs.com/zhaof/tag/爬虫/default.html?page=2) 

[优秀博客 - 简书](https://www.jianshu.com/p/5d7366ac16ec) 

