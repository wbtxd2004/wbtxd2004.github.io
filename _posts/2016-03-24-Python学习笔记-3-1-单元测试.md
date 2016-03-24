---
layout: post
category: Python
title:  Python学习笔记-补充知识-[1]单元测试
date:   2016-03-24 11:05:05
tagline: by WuBin 武斌
tags: [Python]
published: true
author: 武斌

---

本篇主要介绍关于计算机单元测试的一些基础知识。

<!--more-->

# 定义

在计算机编程中，单元测试（英语：Unit Testing）又称为模块测试, 是针对程序模块（软件设计的最小单位）来进行正确性检验的测试工作。程序单元是应用的最小可测试部件。在过程化编程中，一个单元就是单个程序、函数、过程等；对于面向对象编程，最小单元就是方法，包括基类（超类）、抽象类、或者派生类（子类）中的方法。

通常来说，程序员每修改一次程序就会进行最少一次单元测试，在编写程序的过程中前后很可能要进行多次单元测试，以证实程序达到软件规格书要求的工作目标，没有程序错误；虽然单元测试不是什么必须的，但也不坏，这牵涉到项目管理的政策决定。

每个理想的测试案例独立于其它案例；为测试时隔离模块，经常使用stubs、mock[1]或fake等测试马甲程序。单元测试通常由软件开发人员编写，用于确保他们所写的代码符合软件需求和遵循开发目标。它的实施方式可以是非常手动的（通过纸笔），或者是做成构建自动化的一部分。

# 介绍
单元测试是用来对一个模块、一个函数或者一个类来进行正确性检验的测试工作。

比如对函数abs()，我们可以编写出以下几个测试用例：

输入正数，比如1、1.2、0.99，期待返回值与输入相同；

输入负数，比如-1、-1.2、-0.99，期待返回值与输入相反；

输入0，期待返回0；

输入非数值类型，比如None、[]、{}，期待抛出TypeError。

把上面的测试用例放到一个测试模块里，就是一个完整的单元测试。

如果单元测试通过，说明我们测试的这个函数能够正常工作。如果单元测试不通过，要么函数有bug，要么测试条件输入不正确，总之，需要修复使单元测试能够通过。

单元测试通过后有什么意义呢？如果我们对abs()函数代码做了修改，只需要再跑一遍单元测试，如果通过，说明我们的修改不会对abs()函数原有的行为造成影响，如果测试不通过，说明我们的修改与原有行为不一致，要么修改代码，要么修改测试。

这种以测试为驱动的开发模式最大的好处就是确保一个程序模块的行为符合我们设计的测试用例。在将来修改的时候，可以极大程度地保证该模块行为仍然是正确的。

我们来编写一个Dict类，这个类的行为和dict一致，但是可以通过属性来访问，用起来就像下面这样：

	>>> d = Dict(a=1, b=2)
	>>> d['a']
	1
	>>> d.a
	1
**mydict.py**代码如下：

	class Dict(dict):
	
	    def __init__(self, **kw):
	        super(Dict, self).__init__(**kw)
	
	    def __getattr__(self, key):
	        try:
	            return self[key]
	        except KeyError:
	            raise AttributeError(r"'Dict' object has no attribute '%s'" % key)
	
	    def __setattr__(self, key, value):
	        self[key] = value
为了编写单元测试，我们需要引入Python自带的unittest模块，编写mydict_test.py如下：

	import unittest
	
	from mydict import Dict
	
	class TestDict(unittest.TestCase):
	
	    def test_init(self):
	        d = Dict(a=1, b='test')
	        self.assertEquals(d.a, 1)
	        self.assertEquals(d.b, 'test')
	        self.assertTrue(isinstance(d, dict))
	
	    def test_key(self):
	        d = Dict()
	        d['key'] = 'value'
	        self.assertEquals(d.key, 'value')
	
	    def test_attr(self):
	        d = Dict()
	        d.key = 'value'
	        self.assertTrue('key' in d)
	        self.assertEquals(d['key'], 'value')
	
	    def test_keyerror(self):
	        d = Dict()
	        with self.assertRaises(KeyError):
	            value = d['empty']
	
	    def test_attrerror(self):
	        d = Dict()
	        with self.assertRaises(AttributeError):
	            value = d.empty
编写单元测试时，我们需要编写一个测试类，从unittest.TestCase继承。

以**test**开头的方法就是测试方法，不以**test**开头的方法不被认为是测试方法，测试的时候不会被执行。

对每一类测试都需要编写一个test_xxx()方法。由于unittest.TestCase提供了很多内置的条件判断，我们只需要调用这些方法就可以断言输出是否是我们所期望的。最常用的断言就是assertEquals()：

	self.assertEquals(abs(-1), 1) # 断言函数返回的结果与1相等
另一种重要的断言就是期待抛出指定类型的Error，比如通过d['empty']访问不存在的key时，断言会抛出KeyError：

	with self.assertRaises(KeyError):
	    value = d['empty']
而通过d.empty访问不存在的key时，我们期待抛出AttributeError：

	with self.assertRaises(AttributeError):
	    value = d.empty
运行单元测试

一旦编写好单元测试，我们就可以运行单元测试。最简单的运行方式是在mydict_test.py的最后加上两行代码：

	if __name__ == '__main__':
	    unittest.main()
这样就可以把mydict_test.py当做正常的python脚本运行：

	$ python mydict_test.py
另一种更常见的方法是在命令行通过参数-m unittest直接运行单元测试：

	$ python -m unittest mydict_test
	.....
	--------------------------------------------------------------
	Ran 5 tests in 0.000s
	
	OK
这是推荐的做法，因为这样可以一次批量运行很多单元测试，并且，有很多工具可以自动来运行这些单元测试。

setUp与tearDown

可以在单元测试中编写两个特殊的setUp()和tearDown()方法。这两个方法会分别在每调用一个测试方法的前后分别被执行。

setUp()和tearDown()方法有什么用呢？设想你的测试需要启动一个数据库，这时，就可以在setUp()方法中连接数据库，在tearDown()方法中关闭数据库，这样，不必在每个测试方法中重复相同的代码：

	class TestDict(unittest.TestCase):
	
	    def setUp(self):
	        print 'setUp...'
	
	    def tearDown(self):
	        print 'tearDown...'
可以再次运行测试看看每个测试方法调用前后是否会打印出setUp...和tearDown...。

## 小结

单元测试可以有效地测试某个程序模块的行为，是未来重构代码的信心保证。

单元测试的测试用例要覆盖常用的输入组合、边界条件和异常。

单元测试代码要非常简单，如果测试代码太复杂，那么测试代码本身就可能有bug。

单元测试通过了并不意味着程序就没有bug了，但是不通过程序肯定有bug。




# 参考文档
1. [廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014317848428125ae6aa24068b4c50a7e71501ab275d52000)
2. [慕课网](http://www.imooc.com/learn/317)
3. [Python官方文档](https://docs.python.org/3/)
4. [维基百科](https://zh.wikipedia.org/wiki/%E5%8D%95%E5%85%83%E6%B5%8B%E8%AF%95)