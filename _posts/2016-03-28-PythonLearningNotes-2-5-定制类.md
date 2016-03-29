---
layout: post
category: Python
title:  Python学习笔记-进阶篇-[5]定制类
date:   2016-03-29 15:00
tagline: by WuBin 武斌
tags: [Python]
published: true
author: 武斌

---

看到类似\_\_slots\_\_这种形如\_\_xxx\_\_的变量或者函数名就要注意，这些在Python中是有特殊用途的。

\_\_slots\_\_我们已经知道怎么用了，\_\_len\_\_()方法我们也知道是为了能让class作用于len()函数。

除此之外，Python的class中还有许多这样有特殊用途的函数，可以帮助我们定制类。

<!--more-->

# \_\_str\_\_和\_\_repr\_\_

如果要把一个类的实例变成str，就需要实现特殊方法\_\_str\_\_()：

	class Person(object):
	    def __init__(self, name, gender):
	        self.name = name
	        self.gender = gender
	    def __str__(self):
	        return '(Person: %s, %s)' % (self.name, self.gender)

现在，在交互式命令行下用 print 试试：

	>>> p = Person('Bob', 'male')
	>>> print p
	(Person: Bob, male)

但是，如果直接敲变量 p：

	>>> p
	<main.Person object at 0x10c941890>

似乎__str__() 不会被调用。

因为 Python 定义了\_\_str\_\_()和\_\_repr\_\_()两种方法，\_\_str\_\_()用于显示给用户，而\_\_repr\_\_()用于显示给开发人员。

有一个偷懒的定义__repr__的方法：

	class Person(object):
	    def __init__(self, name, gender):
	        self.name = name
	        self.gender = gender
	    def __str__(self):
	        return '(Person: %s, %s)' % (self.name, self.gender)
	    __repr__ = __str__

# \_\_cmp\_\_

对 int、str 等内置数据类型排序时，Python的 sorted() 按照默认的比较函数 cmp 排序，但是，如果对一组 Student 类的实例排序时，就必须提供我们自己的特殊方法 \_\_cmp\_\_()：

	class Student(object):
	    def __init__(self, name, score):
	        self.name = name
	        self.score = score
	    def __str__(self):
	        return '(%s: %s)' % (self.name, self.score)
	    __repr__ = __str__
	
	    def __cmp__(self, s):
	        if self.name < s.name:
	            return -1
	        elif self.name > s.name:
	            return 1
	        else:
	            return 0

上述 Student 类实现了__cmp__()方法，__cmp__用实例自身self和传入的实例 s 进行比较，如果 self 应该排在前面，就返回 -1，如果 s 应该排在前面，就返回1，如果两者相当，返回 0。

Student类实现了按name进行排序：

	>>> L = [Student('Tim', 99), Student('Bob', 88), Student('Alice', 77)]
	>>> print sorted(L)
	[(Alice: 77), (Bob: 88), (Tim: 99)]

注意: 如果list不仅仅包含 Student 类，则 \_\_cmp\_\_ 可能会报错：

	L = [Student('Tim', 99), Student('Bob', 88), 100, 'Hello']
	print sorted(L)

请思考如何解决。

## 任务

请修改 Student 的 \_\_cmp\_\_ 方法，让它按照分数从高到底排序，分数相同的按名字排序。

需要先比较 score，在 score 相等的情况下，再比较 name。

参考代码:

	class Student(object):
	    def __init__(self, name, score):
	        self.name = name
	        self.score = score
	
	    def __str__(self):
	        return '(%s: %s)' % (self.name, self.score)
	
	    __repr__ = __str__
	
	    def __cmp__(self, s):
	        if self.score == s.score:
	            return cmp(self.name, s.name)
	        return -cmp(self.score, s.score)
	
	L = [Student('Tim', 99), Student('Bob', 88), Student('Alice', 99)]
	print sorted(L)

# \_\_len\_\_

如果一个类表现得像一个list，要获取有多少个元素，就得用 len() 函数。

要让 len() 函数工作正常，类必须提供一个特殊方法\_\_len\_\_()，它返回元素的个数。

例如，我们写一个 Students 类，把名字传进去：

	class Students(object):
	    def __init__(self, *args):
	        self.names = args
	    def __len__(self):
	        return len(self.names)

只要正确实现了__len__()方法，就可以用len()函数返回Students实例的“长度”：

	>>> ss = Students('Bob', 'Alice', 'Tim')
	>>> print len(ss)
	3
	
## 任务

斐波那契数列是由 0, 1, 1, 2, 3, 5, 8...构成。

请编写一个Fib类，Fib(10)表示数列的前10个元素，print Fib(10) 可以打印出数列的前 10 个元素，len(Fib(10))可以正确返回数列的个数10。

需要根据num计算出斐波那契数列的前N个元素。

参考代码:

	class Fib(object):
	    def __init__(self, num):
	        a, b, L = 0, 1, []
	        for n in range(num):
	            L.append(a)
	            a, b = b, a + b
	        self.numbers = L
	
	    def __str__(self):
	        return str(self.numbers)
	
	    __repr__ = __str__
	
	    def __len__(self):
	        return len(self.numbers)
	
	f = Fib(10)
	print f
	print len(f)

# 数学运算

Python 提供的基本数据类型 int、float 可以做整数和浮点的四则运算以及乘方等运算。

但是，四则运算不局限于int和float，还可以是有理数、矩阵等。

要表示有理数，可以用一个Rational类来表示：

	class Rational(object):
	    def __init__(self, p, q):
	        self.p = p
	        self.q = q

p、q 都是整数，表示有理数 p/q。

如果要让**Rational进行+运算**，需要正确实现\_\_add\_\_：

	class Rational(object):
	    def __init__(self, p, q):
	        self.p = p
	        self.q = q
	    def __add__(self, r):
	        return Rational(self.p * r.q + self.q * r.p, self.q * r.q)
	    def __str__(self):
	        return '%s/%s' % (self.p, self.q)
	    __repr__ = __str__

现在可以试试有理数加法：

	>>> r1 = Rational(1, 3)
	>>> r2 = Rational(1, 2)
	>>> print r1 + r2
	5/6


# 类型转换

Rational类实现了有理数运算，但是，如果要把结果转为 int 或 float 怎么办？

考察整数和浮点数的转换：

	>>> int(12.34)
	12
	>>> float(12)
	12.0

如果要把 Rational 转为 int，应该使用：

	r = Rational(12, 5)
	n = int(r)

要让int()函数正常工作，只需要实现特殊方法\_\_int\_\_():

	class Rational(object):
	    def __init__(self, p, q):
	        self.p = p
	        self.q = q
	    def __int__(self):
	        return self.p // self.q

结果如下：

	>>> print int(Rational(7, 2))
	3
	>>> print int(Rational(1, 3))
	0

同理，要让float()函数正常工作，只需要实现特殊方法\_\_float\_\_()。

# @property

考察 Student 类：

	class Student(object):
	    def __init__(self, name, score):
	        self.name = name
	        self.score = score

当我们想要修改一个 Student 的 scroe 属性时，可以这么写：

	s = Student('Bob', 59)
	s.score = 60

但是也可以这么写：

	s.score = 1000

显然，直接给属性赋值无法检查分数的有效性。

如果利用两个方法：

	class Student(object):
	    def __init__(self, name, score):
	        self.name = name
	        self.__score = score
	    def get_score(self):
	        return self.__score
	    def set_score(self, score):
	        if score < 0 or score > 100:
	            raise ValueError('invalid score')
	        self.__score = score

这样一来，s.set_score(1000) 就会报错。

这种使用 get/set 方法来封装对一个属性的访问在许多面向对象编程的语言中都很常见。

但是写 s.get_score() 和 s.set_score() 没有直接写 s.score 来得直接。

有没有两全其美的方法？----有。

因为Python支持高阶函数，在函数式编程中我们介绍了装饰器函数，可以用装饰器函数把 get/set 方法“装饰”成属性调用：

	class Student(object):
	    def __init__(self, name, score):
	        self.name = name
	        self.__score = score
	    @property
	    def score(self):
	        return self.__score
	    @score.setter
	    def score(self, score):
	        if score < 0 or score > 100:
	            raise ValueError('invalid score')
	        self.__score = score

注意: 第一个score(self)是get方法，用**@property**装饰，第二个score(self, score)是set方法，用@score.setter装饰，@score.setter是前一个@property装饰后的副产品。

现在，就可以像使用属性一样设置score了：

	>>> s = Student('Bob', 59)
	>>> s.score = 60
	>>> print s.score
	60
	>>> s.score = 1000
	Traceback (most recent call last):
	  ...
	ValueError: invalid score

说明对 score 赋值实际调用的是 set方法。

# \_\_slots\_\_

由于Python是动态语言，任何实例在运行期都可以动态地添加属性。

如果要限制添加的属性，例如，Student类只允许添加 name、gender和score 这3个属性，就可以利用Python的一个特殊的__slots__来实现。

顾名思义，__slots__是指一个类允许的属性列表：

	class Student(object):
	    __slots__ = ('name', 'gender', 'score')
	    def __init__(self, name, gender, score):
	        self.name = name
	        self.gender = gender
	        self.score = score

现在，对实例进行操作：

	>>> s = Student('Bob', 'male', 59)
	>>> s.name = 'Tim' # OK
	>>> s.score = 99 # OK
	>>> s.grade = 'A'
	Traceback (most recent call last):
	  ...
	AttributeError: 'Student' object has no attribute 'grade'

\_\_slots\_\_的目的是限制当前类所能拥有的属性，如果不需要添加任意动态的属性，使用\_\_slots\_\_也能节省内存。

# \_\_call\_\_

在Python中，函数其实是一个对象：

	>>> f = abs
	>>> f.__name__
	'abs'
	>>> f(-123)
	123

由于 f 可以被调用，所以，f 被称为可调用对象。

所有的函数都是可调用对象。

一个类实例也可以变成一个可调用对象，只需要实现一个特殊方法\_\_call\_\_()。

我们把 Person 类变成一个可调用对象：

	class Person(object):
	    def __init__(self, name, gender):
	        self.name = name
	        self.gender = gender
	
	    def __call__(self, friend):
	        print 'My name is %s...' % self.name
	        print 'My friend is %s...' % friend
	        
现在可以对 Person 实例直接调用：

	>>> p = Person('Bob', 'male')
	>>> p('Tim')
	My name is Bob...
	My friend is Tim...

单看 p('Tim') 你无法确定 p 是一个函数还是一个类实例，所以，在Python中，函数也是对象，对象和函数的区别并不显著。

# 参考资料

1. [廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014317848428125ae6aa24068b4c50a7e71501ab275d52000)
2. [慕课网](http://www.imooc.com/learn/317)
3. [Python官方文档](https://docs.python.org/3/)