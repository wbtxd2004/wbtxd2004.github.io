---
layout: post
category: Python
title:  Python学习笔记-基础篇-[7]高级特性
date:   2016-03-27 12:16:00
tagline: by WuBin 武斌
tags: [Python]
published: true
author: 武斌

---

掌握了Python的数据类型、语句和函数，基本上就可以编写出很多有用的程序了。但是在Python中，代码不是越多越好，而是越少越好。代码不是越复杂越好，而是越简单越好。基于这一思想，我们来介绍Python中非常有用的高级特性，1行代码能实现的功能，决不写5行代码。请始终牢记，代码越少，开发效率越高。

<!--more-->

# 切片

## 对list进行切片

取一个list的部分元素是非常常见的操作。比如，一个list如下：

	>>> L = ['Adam', 'Lisa', 'Bart', 'Paul']

取前3个元素，应该怎么做？

笨办法：

	>>> [L[0], L[1], L[2]]
	['Adam', 'Lisa', 'Bart']

之所以是笨办法是因为扩展一下，取前N个元素就没辙了。

取前N个元素，也就是索引为0-(N-1)的元素，可以用循环：

	>>> r = []
	>>> n = 3
	>>> for i in range(n):
	...     r.append(L[i])
	... 
	>>> r
	['Adam', 'Lisa', 'Bart']

对这种经常取指定索引范围的操作，用循环十分繁琐，因此，Python提供了切片（Slice）操作符，能大大简化这种操作。

对应上面的问题，取前3个元素，用一行代码就可以完成切片：

	>>> L[0:3]
	['Adam', 'Lisa', 'Bart']

L[0:3]表示，从索引0开始取，直到索引3为止，但不包括索引3。即索引0，1，2，正好是3个元素。

如果第一个索引是0，还可以省略：

	>>> L[:3]
	['Adam', 'Lisa', 'Bart']

也可以从索引1开始，取出2个元素出来：

	>>> L[1:3]
	['Lisa', 'Bart']

只用一个 : ，表示从头到尾：

	>>> L[:]
	['Adam', 'Lisa', 'Bart', 'Paul']

因此，L[:]实际上复制出了一个新list。

切片操作还可以指定第三个参数：

	>>> L[::2]
	['Adam', 'Bart']

第三个参数表示每N个取一个，上面的 L[::2] 会每两个元素取出一个来，也就是隔一个取一个。

把list换成tuple，切片操作完全相同，只是切片的结果也变成了tuple。

## 倒序切片

对于list，既然Python支持L[-1]取倒数第一个元素，那么它同样支持倒数切片，试试：

	>>> L = ['Adam', 'Lisa', 'Bart', 'Paul']

	>>> L[-2:]
	['Bart', 'Paul']

	>>> L[:-2]
	['Adam', 'Lisa']
	
	>>> L[-3:-1]
	['Lisa', 'Bart']
	
	>>> L[-4:-1:2]
	['Adam', 'Bart']

记住倒数第一个元素的索引是-1。倒序切片包含起始索引，不包含结束索引。

## 对字符串切片

字符串 'xxx'和 Unicode字符串 u'xxx'也可以看成是一种list，每个元素就是一个字符。因此，字符串也可以用切片操作，只是操作结果仍是字符串：

	>>> 'ABCDEFG'[:3]
	'ABC'
	>>> 'ABCDEFG'[-3:]
	'EFG'
	>>> 'ABCDEFG'[::2]
	'ACEG'

在很多编程语言中，针对字符串提供了很多各种截取函数，其实目的就是对字符串切片。Python没有针对字符串的截取函数，只需要切片一个操作就可以完成，非常简单。

# 迭代

## 什么是迭代

在Python中，如果给定一个list或tuple，我们可以通过for循环来遍历这个list或tuple，这种遍历我们成为迭代（Iteration）。

在Python中，迭代是通过 for ... in 来完成的，而很多语言比如C或者Java，迭代list是通过下标完成的，比如Java代码：

	for (i=0; i<list.length; i++) {
	    n = list[i];
	}

可以看出，Python的for循环抽象程度要高于Java的for循环。

**因为 Python 的 for循环不仅可以用在list或tuple上，还可以作用在其他任何可迭代对象上。**

因此，迭代操作就是对于一个集合，无论该集合是有序还是无序，我们用 for 循环总是可以依次取出集合的每一个元素。

	注意: 集合是指包含一组元素的数据结构，我们已经介绍的包括：
	1. 有序集合：list，tuple，str和unicode；
	2. 无序集合：set
	3. 无序集合并且具有 key-value 对：dict

而迭代是一个动词，它指的是一种操作，在Python中，就是 for 循环。

迭代与按下标访问数组最大的不同是，后者是一种具体的迭代实现方式，而前者只关心迭代结果，根本不关心迭代内部是如何实现的。

## 索引迭代

Python中，**迭代永远是取出元素本身，而非元素的索引**。

对于有序集合，元素确实是有索引的。有的时候，我们确实想在 for 循环中拿到索引，怎么办？

方法是使用 **enumerate()** 函数：

	>>> L = ['Adam', 'Lisa', 'Bart', 'Paul']
	>>> for index, name in enumerate(L):
	...     print index, '-', name
	... 
	0 - Adam
	1 - Lisa
	2 - Bart
	3 - Paul

使用 enumerate() 函数，我们可以在for循环中同时绑定索引index和元素name。但是，这不是 enumerate() 的特殊语法。实际上，enumerate() 函数把：

	['Adam', 'Lisa', 'Bart', 'Paul']

变成了类似：

	[(0, 'Adam'), (1, 'Lisa'), (2, 'Bart'), (3, 'Paul')]

因此，迭代的每一个元素实际上是一个tuple：

	for t in enumerate(L):
	    index = t[0]
	    name = t[1]
	    print index, '-', name

如果我们知道每个tuple元素都包含两个元素，for循环又可以进一步简写为：

	for index, name in enumerate(L):
	    print index, '-', name

这样不但代码更简单，而且还少了两条赋值语句。

可见，索引迭代也不是真的按索引访问，而是由 enumerate() 函数自动把每个元素变成 (index, element) 这样的tuple，再迭代，就同时获得了索引和元素本身。

## 迭代dict的value

**我们已经了解了dict对象本身就是可迭代对象**，用 for 循环直接迭代 dict，可以每次拿到dict的一个key。

如果我们希望迭代dict对象的value，应该怎么做？

dict 对象有一个**values()**方法，这个方法把dict转换成一个包含所有value的list，这样，我们迭代的就是 dict的每一个 value：

	d = { 'Adam': 95, 'Lisa': 85, 'Bart': 59 }
	print d.values()
	# [85, 95, 59]
	for v in d.values():
	    print v
	# 85
	# 95
	# 59

如果仔细阅读Python的文档，还可以发现，dict除了values()方法外，还有一个**itervalues()**方法，用 itervalues() 方法替代 values() 方法，迭代效果完全一样：

	d = { 'Adam': 95, 'Lisa': 85, 'Bart': 59 }
	print d.itervalues()
	# <dictionary-valueiterator object at 0x106adbb50>
	for v in d.itervalues():
	    print v
	# 85
	# 95
	# 59

那这两个方法有何不同之处呢？

1. values() 方法实际上把一个 dict 转换成了包含 value 的list。

2. 但是 itervalues() 方法不会转换，它会在迭代过程中依次从 dict 中取出 value，所以 itervalues() 方法比 values() 方法节省了生成 list 所需的内存。

3. 打印 itervalues() 发现它返回一个 <dictionary-valueiterator> 对象，这说明在Python中，**for 循环可作用的迭代对象远不止 list，tuple，str，unicode，dict等**，任何可迭代对象都可以作用于for循环，而内部如何迭代我们通常并不用关心。

**如果一个对象说自己可迭代，那我们就直接用 for 循环去迭代它，可见，迭代是一种抽象的数据操作，它不对迭代对象内部的数据有任何要求**。

## 迭代dict的key和value

我们了解了如何迭代 dict 的key和value，那么，在一个 for 循环中，能否同时迭代 key和value？答案是肯定的。

首先，我们看看 dict 对象的 items() 方法返回的值：

	>>> d = { 'Adam': 95, 'Lisa': 85, 'Bart': 59 }
	>>> print d.items()
	[('Lisa', 85), ('Adam', 95), ('Bart', 59)]

可以看到，items() 方法把dict对象转换成了包含tuple的list，我们对这个list进行迭代，可以同时获得key和value：

	>>> for key, value in d.items():
	...     print key, ':', value
	... 
	Lisa : 85
	Adam : 95
	Bart : 59

和 values() 有一个 itervalues() 类似， items() 也有一个对应的 iteritems()，iteritems() 不把dict转换成list，而是在迭代过程中不断给出 tuple，所以， iteritems() 不占用额外的内存。

# 列表生成式

## 生成列表

要生成list [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]，我们可以用range(1, 11)：

	>>> range(1, 11)
	[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

但如果要生成[1x1, 2x2, 3x3, ..., 10x10]怎么做？方法一是循环：

	>>> L = []
	>>> for x in range(1, 11):
	...    L.append(x * x)
	... 
	>>> L
	[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

但是循环太繁琐，而列表生成式则可以用一行语句代替循环生成上面的list：

	>>> [x * x for x in range(1, 11)]
	[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

这种写法就是Python特有的列表生成式。利用列表生成式，可以以非常简洁的代码生成 list。

写列表生成式时，把要生成的元素 x * x 放到前面，后面跟 for 循环，就可以把list创建出来，十分有用，多写几次，很快就可以熟悉这种语法。

## 复杂表达式

使用for循环的迭代不仅可以迭代普通的list，还可以迭代dict。

假设有如下的dict：

	d = { 'Adam': 95, 'Lisa': 85, 'Bart': 59 }

完全可以通过一个复杂的列表生成式把它变成一个 HTML 表格：

	tds = ['<tr><td>%s</td><td>%s</td></tr>' % (name, score) for name, score in d.iteritems()]
	print '<table>'
	print '<tr><th>Name</th><th>Score</th><tr>'
	print '\n'.join(tds)
	print '</table>'

注：字符串可以通过 % 进行格式化，用指定的参数替代 %s。字符串的join()方法可以把一个 list 拼接成一个字符串。

把打印出来的结果保存为一个html文件，就可以在浏览器中看到效果了：

	<table border="1">
	<tr><th>Name</th><th>Score</th><tr>
	<tr><td>Lisa</td><td>85</td></tr>
	<tr><td>Adam</td><td>95</td></tr>
	<tr><td>Bart</td><td>59</td></tr>
	</table>

<table border="1">
<tr><th>Name</th><th>Score</th><tr>
<tr><td>Lisa</td><td>85</td></tr>
<tr><td>Adam</td><td>95</td></tr>
<tr><td>Bart</td><td>59</td></tr>
</table>

## 条件过滤

列表生成式的 for 循环后面还可以加上 if 判断。例如：

	>>> [x * x for x in range(1, 11)]
	[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

如果我们只想要偶数的平方，不改动 range()的情况下，可以加上 if 来筛选：

	>>> [x * x for x in range(1, 11) if x % 2 == 0]
	[4, 16, 36, 64, 100]

有了 if 条件，只有 if 判断为 True 的时候，才把循环的当前元素添加到列表中。

## 多层表达式

for循环可以嵌套，因此，在列表生成式中，也可以用多层 for 循环来生成列表。

对于字符串 'ABC' 和 '123'，可以使用两层循环，生成全排列：

	>>> [m + n for m in 'ABC' for n in '123']
	['A1', 'A2', 'A3', 'B1', 'B2', 'B3', 'C1', 'C2', 'C3']

翻译成循环代码就像下面这样：

	L = []
	for m in 'ABC':
	    for n in '123':
	        L.append(m + n)


# 参考文档
1. [廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014317848428125ae6aa24068b4c50a7e71501ab275d52000)
2. [慕课网](http://www.imooc.com/learn/317)
3. [Python官方文档](https://docs.python.org/3/)
