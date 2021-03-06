---
layout: post
category: Python
title:  Python学习笔记-基础篇-[5]Dict和Set数据类型
date:   2016-03-27 01:11:01
tagline: by WuBin 武斌
tags: [Python]
published: true
author: 武斌

---

本篇主要介绍了Python的Dict(字典)和Set(集合)类型。

<!--more-->

# 什么是dict

我们已经知道，list和tuple可以用来表示顺序集合，例如班里同学的名字：

	['Adam', 'Lisa', 'Bart']

或者考试的成绩列表：

	[95, 85, 59]

但是，要根据名字找到对应的成绩，用两个list表示就不方便。

如果把名字和分数关联起来，组成类似的查找表：

	'Adam' ==> 95
	'Lisa' ==> 85
	'Bart' ==> 59

给定一个名字，就可以直接查到分数。

Python的dict就是专门干这件事的。用dict表示“名字”-“成绩”的查找表如下：

	d = {
	    'Adam': 95,
	    'Lisa': 85,
	    'Bart': 59
	}

我们把名字称为key，对应的成绩称为value，dict就是通过key来查找value。

花括号{}表示这是一个dict，然后按照key: value, 写出来即可。最后一个 key: value 的逗号可以省略。

由于dict也是集合，len() 函数可以计算任意集合的大小：

	>>> len(d)
	3

注意: 一个 key-value 算一个，因此，dict大小为3。

# 访问dict

我们已经能创建一个dict，用于表示名字和成绩的对应关系：

	d = {
	    'Adam': 95,
	    'Lisa': 85,
	    'Bart': 59
	}

那么，如何根据名字来查找对应的成绩呢？

可以简单地使用d[key]的形式来查找对应的value，这和list很像，不同之处是，list必须使用索引返回对应的元素，而dict使用key：

	>>> print d['Adam']
	95
	>>> print d['Paul']
	Traceback (most recent call last):
	  File "index.py", line 11, in <module>
	    print d['Paul']
	KeyError: 'Paul'

注意: 通过key访问dict的value，只要key存在，dict就返回对应的value。如果key不存在，会直接报错：KeyError。

要避免 KeyError 发生，有两个办法：

1. 先判断一下 key 是否存在，用 in 操作符：

		if 'Paul' in d:
		    print d['Paul']

	如果 'Paul' 不存在，if语句判断为False，自然不会执行 print d['Paul'] ，从而避免了错误。

2. 使用dict本身提供的一个 get 方法，在Key不存在的时候，返回None：

		>>> print d.get('Bart')
		59
		>>> print d.get('Paul')
		None

# dict的特点

**dict的第一个特点是查找速度快，无论dict有10个元素还是10万个元素，查找速度都一样**。而list的查找速度随着元素增加而逐渐下降。

不过dict的查找速度快不是没有代价的，**dict的缺点是占用内存大，还会浪费很多内容**，list正好相反，占用内存小，但是查找速度慢。

由于dict是按key查找，所以在一个dict中，**key不能重复**。

**dict的第二个特点就是存储的key-value序对是没有顺序的**！这和list不一样：

	d = {
	    'Adam': 95,
	    'Lisa': 85,
	    'Bart': 59
	}
	
当我们试图打印这个dict时：

	>>> print d
	{'Lisa': 85, 'Adam': 95, 'Bart': 59}

打印的顺序不一定是我们创建时的顺序，而且不同的机器打印的顺序都可能不同，这说明dict内部是**无序**的，不能用dict存储有序的集合。

**dict的第三个特点是作为key的元素必须不可变**，Python的基本类型如字符串、整数、浮点数都是不可变的，都可以作为key。但是list是可变的，就不能作为key。

可以试试用list作为key时会报什么样的错误。

不可变这个限制仅作用于key，value是否可变无所谓：

	{
	    '123': [1, 2, 3],  # key 是 str，value是list
	    123: '123',  # key 是 int，value 是 str
	    ('a', 'b'): True  # key 是 tuple，并且tuple的每个元素都是不可变对象，value是 boolean
	}
	
最常用的key还是字符串，因为用起来最方便。

# 更新dict

dict是可变的，也就是说，我们可以随时往dict中添加新的key-value。比如已有dict：

	d = {
	    'Adam': 95,
	    'Lisa': 85,
	    'Bart': 59
	}

要把新同学'Paul'的成绩72加进去，用赋值语句：

	>>> d['Paul'] = 72

再看看dict的内容：

	>>> print d
	{'Lisa': 85, 'Paul': 72, 'Adam': 95, 'Bart': 59}

如果key已经存在，则赋值会用新的value替换掉原来的value：

	>>> d['Bart'] = 60
	>>> print d
	{'Lisa': 85, 'Paul': 72, 'Adam': 95, 'Bart': 60}

# 遍历dict

由于dict也是一个集合，所以，遍历dict和遍历list类似，都可以通过for循环实现。

直接使用for循环可以遍历dict的key：

	>>> d = { 'Adam': 95, 'Lisa': 85, 'Bart': 59 }
	>>> for key in d:
	...     print key
	... 
	Lisa
	Adam
	Bart

由于通过key可以获取对应的value，因此，在循环体内，可以获取到value的值。

# 什么是set

**dict的作用是建立一组key和一组value的映射关系，dict的key是不能重复的。**

有的时候，我们只想要dict的key，不关心key对应的value，目的就是保证这个集合的元素不会重复，这时，set就派上用场了。

**set持有一系列元素，这一点和list很像，但是set的元素没有重复，而且是无序的，这点和dict的key很像。**

创建set的方式是调用set()并传入一个list，list的元素将作为set的元素：

	>>> s = set(['A', 'B', 'C'])

可以查看 set 的内容：

	>>> print s
	set(['A', 'C', 'B'])

请注意，上述打印的形式类似list， 但它不是list，仔细看还可以发现，打印的顺序和原始 list的顺序有可能是不同的，因为set内部存储的元素是无序的。

因为**set不能包含重复的元素**，所以，当我们传入包含重复元素的list会怎么样呢？

	>>> s = set(['A', 'B', 'C', 'C'])
	>>> print s
	set(['A', 'C', 'B'])
	>>> len(s)
	3

结果显示，set会自动去掉重复的元素，原来的list有4个元素，但set只有3个元素。

# set的特点

**set的内部结构和dict很像，唯一区别是不存储value**，因此，判断一个元素是否在set中速度很快。

**set存储的元素和dict的key类似，必须是不变对象**，因此，任何可变对象是不能放入set中的。

最后，**set存储的元素也是没有顺序的**。

set的这些特点，可以应用在哪些地方呢？

星期一到星期日可以用字符串'MON', 'TUE', ... 'SUN'表示。

假设我们让用户输入星期一至星期日的某天，如何判断用户的输入是否是一个有效的星期呢？

可以用if语句判断，但这样做非常繁琐：

	x = '???' # 用户输入的字符串
	if x!= 'MON' and x!= 'TUE' and x!= 'WED' ... and x!= 'SUN':
	    print 'input error'
	else:
	    print 'input ok'

注意：if语句中的...表示没有列出的其它星期名称，测试时，请输入完整。

如果事先创建好一个set，包含'MON' ~ 'SUN'：

	weekdays = set(['MON', 'TUE', 'WED', 'THU', 'FRI', 'SAT', 'SUN'])

再判断输入是否有效，只需要判断该字符串是否在set中：

	x = '???' # 用户输入的字符串
	if x in weekdays:
	    print 'input ok'
	else:
	    print 'input error'

这样一来，代码就简单多了。

# 遍历set

由于set也是一个集合，所以，遍历set和遍历list类似，都可以通过for循环实现。

直接使用for循环可以遍历set的元素：

	>>> s = set(['Adam', 'Lisa', 'Bart'])
	>>> for name in s:
	...     print name
	... 
	Lisa
	Adam
	Bart

**注意: 观察for循环在遍历set时，元素的顺序和list的顺序很可能是不同的，而且不同的机器上运行的结果也可能不同。**

# 更新set

由于**set存储的是一组不重复的无序元素**，因此，更新set主要做两件事：

**一是把新的元素添加到set中，二是把已有元素从set中删除。**

添加元素时，用set的add()方法：

	>>> s = set([1, 2, 3])
	>>> s.add(4)
	>>> print s
	set([1, 2, 3, 4])

如果添加的元素已经存在于set中，add()不会报错，但是不会加进去了：

	>>> s = set([1, 2, 3])
	>>> s.add(3)
	>>> print s
	set([1, 2, 3])

删除set中的元素时，用set的remove()方法：

	>>> s = set([1, 2, 3, 4])
	>>> s.remove(4)
	>>> print s
	set([1, 2, 3])

如果删除的元素不存在set中，remove()会报错：

	>>> s = set([1, 2, 3])
	>>> s.remove(4)
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	KeyError: 4
	
所以用add()可以直接添加，而remove()前需要判断。

# 参考文档
1. [廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014317848428125ae6aa24068b4c50a7e71501ab275d52000)
2. [慕课网](http://www.imooc.com/learn/317)
3. [Python官方文档](https://docs.python.org/3/)
