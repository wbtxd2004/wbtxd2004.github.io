---
layout: post
category: Python
title:  Python学习笔记[1]之高阶函数map()函数。
date:   2016-03-22 09:37:05
tagline: by WuBin 武斌
tags: [Python]
published: true
author: 武斌

---

map()函数是Python内置的高阶函数，它接收一个函数f和一个list，并通过把f依次作用在list的每个元素上，得到一个新的list并返回，可以对list的每一个元素进行计算。

<!--more-->

例如，对于list [1, 2, 3, 4, 5, 6, 7, 8, 9]

如果希望把list的每个元素都作平方，就可以用map()函数：

<img src="{{site.baseurl}}/images/post/2016-03-22/python-map.png" width="600" alt=""/>


因此，我们只需要传入函数f(x)=x*x，就可以利用map()函数完成这个计算：

	def f(x):
	    return x*x
	print map(f, [1, 2, 3, 4, 5, 6, 7, 8, 9])
输出结果：

	[1, 4, 9, 10, 25, 36, 49, 64, 81]
**注意：map()函数不改变原有的 list，而是返回一个新的 list。**

利用map()函数，可以把一个 list 转换为另一个 list，只需要传入转换函数。

**由于list包含的元素可以是任何类型，因此，map() 不仅仅可以处理只包含数值的 list，事实上它可以处理包含任意类型的 list，只要传入的函数f可以处理这种数据类型。**