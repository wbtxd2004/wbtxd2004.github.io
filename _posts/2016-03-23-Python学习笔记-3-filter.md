---
layout: post
category: Python
title:  Python学习笔记[3]之高阶函数filter()函数。
date:   2016-03-22 12:14:05
tagline: by WuBin 武斌
tags: [Python]
published: true
author: 武斌

---

filter()函数是Python内置的另一个有用的高阶函数，filter()函数接收一个函数f和一个list，这个函数f的作用是对每个元素进行判断，返回 True或 False，filter()根据判断结果自动过滤掉不符合条件的元素，返回由符合条件元素组成的新list。

<!--more-->

filter()函数是Python内置的另一个有用的高阶函数，filter()函数接收一个函数f和一个list，这个函数f的作用是对每个元素进行判断，返回 True或 False，filter()根据判断结果自动过滤掉不符合条件的元素，返回由符合条件元素组成的新list。

例如，要从一个list [1, 4, 6, 7, 9, 12, 17]中删除偶数，保留奇数，首先，要编写一个判断奇数的函数：

	def is_odd(x):
    	return x % 2 == 1
然后，利用filter()过滤掉偶数：

	filter(is_odd, [1, 4, 6, 7, 9, 12, 17])
结果：[1, 7, 9, 17]

利用filter()，可以完成很多有用的功能，例如，删除 None 或者空字符串：

	def is_not_empty(s):
	    return s and len(s.strip()) > 0
	filter(is_not_empty, ['test', None, '', 'str', '  ', 'END'])
结果：['test', 'str', 'END']

注意: s.strip(rm) 删除 s 字符串中开头、结尾处的 rm 序列的字符。

当rm为空时，默认删除空白符（包括'\n', '\r', '\t', ' ')，如下：

	a = '     123'
	a.strip()
结果： '123'

	a='\t\t123\r\n'
	a.strip()
结果：'123'