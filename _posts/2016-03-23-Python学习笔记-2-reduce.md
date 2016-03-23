---
layout: post
category: Python
title:  Python学习笔记[2]之高阶函数reduce()函数。
date:   2016-03-22 09:37:05
tagline: by WuBin 武斌
tags: [Python]
published: true
author: 武斌

---

reduce()函数也是Python内置的一个高阶函数。reduce()函数接收的参数和map()类似，一个函数 f，一个list，但行为和map()不同，reduce()传入的函数f必须接收两个参数，reduce()对list的每个元素反复调用函数f，并返回最终结果值。

<!--more-->

reduce()函数也是Python内置的一个高阶函数。reduce()函数接收的参数和map()类似，一个函数 f，一个list，但行为和map()不同，reduce()传入的函数f必须接收两个参数，reduce()对list的每个元素反复调用函数f，并返回最终结果值。

例如，编写一个f函数，接收x和y，返回x和y的和：

	def f(x, y):
	    return x + y
调用 reduce(f, [1, 3, 5, 7, 9])时，reduce函数将做如下计算：

	先计算头两个元素：f(1, 3)，结果为4；
	再把结果和第3个元素计算：f(4, 5)，结果为9；
	再把结果和第4个元素计算：f(9, 7)，结果为16；
	再把结果和第5个元素计算：f(16, 9)，结果为25；
	由于没有更多的元素了，计算结束，返回结果25。
上述计算实际上是对 list 的所有元素求和。虽然Python内置了求和函数sum()，但是，利用reduce()求和也很简单。

reduce()还可以接收第3个可选参数，作为计算的初始值。如果把初始值设为100，计算：

	reduce(f, [1, 3, 5, 7, 9], 100)
结果将变为125，因为第一轮计算是：

计算初始值和第一个元素：f(100, 1)，结果为101。