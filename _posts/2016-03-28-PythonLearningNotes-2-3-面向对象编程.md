---
layout: post
category: Python
title:  Python学习笔记-进阶篇-[3]面向对象编程
date:   2016-03-28 12:59
tagline: by WuBin 武斌
tags: [Python]
published: true
author: 武斌

---

面向对象编程——Object Oriented Programming，简称OOP，是一种程序设计思想。OOP把对象作为程序的基本单元，一个对象包含了数据和操作数据的函数。

<!--more-->

# 基本介绍

面向过程的程序设计把计算机程序视为一系列的命令集合，即一组函数的顺序执行。为了简化程序设计，面向过程把函数继续切分为子函数，即把大块函数通过切割成小块函数来降低系统的复杂度。

而面向对象的程序设计把计算机程序视为一组对象的集合，而每个对象都可以接收其他对象发过来的消息，并处理这些消息，计算机程序的执行就是一系列消息在各个对象之间传递。

在Python中，所有数据类型都可以视为对象，当然也可以自定义对象。自定义的对象数据类型就是面向对象中的类（Class）的概念。

我们以一个例子来说明面向过程和面向对象在程序流程上的不同之处。

假设我们要处理学生的成绩表，为了表示一个学生的成绩，面向过程的程序可以用一个dict表示：

	std1 = { 'name': 'Michael', 'score': 98 }
	std2 = { 'name': 'Bob', 'score': 81 }

而处理学生成绩可以通过函数实现，比如打印学生的成绩：

	def print_score(std):
	    print('%s: %s' % (std['name'], std['score']))

如果采用面向对象的程序设计思想，我们首选思考的不是程序的执行流程，而是Student这种数据类型应该被视为一个对象，这个对象拥有name和score这两个属性（Property）。如果要打印一个学生的成绩，首先必须创建出这个学生对应的对象，然后，给对象发一个print_score消息，让对象自己把自己的数据打印出来。

	class Student(object):
	
	    def __init__(self, name, score):
	        self.name = name
	        self.score = score
	
	    def print_score(self):
	        print('%s: %s' % (self.name, self.score))
	        
给对象发消息实际上就是调用对象对应的关联函数，我们称之为对象的方法（Method）。面向对象的程序写出来就像这样：

	bart = Student('Bart Simpson', 59)
	lisa = Student('Lisa Simpson', 87)
	bart.print_score()
	lisa.print_score()
	
面向对象的设计思想是从自然界中来的，因为在自然界中，类（Class）和实例（Instance）的概念是很自然的。Class是一种抽象概念，比如我们定义的Class——Student，是指学生这个概念，而实例（Instance）则是一个个具体的Student，比如，Bart Simpson和Lisa Simpson是两个具体的Student。

所以，面向对象的设计思想是抽象出Class，根据Class创建Instance。

面向对象的抽象程度又比函数要高，因为一个Class既包含数据，又包含操作数据的方法。

# 定义类并创建实例

在Python中，类通过 class 关键字定义。以 Person 为例，定义一个Person类如下：

	class Person(object):
	    pass

按照 **Python** 的编程习惯，类名以大写字母开头，紧接着是(object)，表示该类是从哪个类继承下来的。类的继承将在后面的章节讲解，现在我们只需要简单地从**object**类继承。

有了Person类的定义，就可以创建出具体的xiaoming、xiaohong等实例。创建实例使用**类名+()**，类似函数调用的形式创建：

	xiaoming = Person()
	xiaohong = Person()

## 任务

请练习定义Person类，并创建出两个实例，打印实例，再比较两个实例是否相等。

要打印实例，直接使用print语句；

要比较两个实例是否相等，用==操作符。

参考代码:

	class Person(object):
	    pass
	xiaoming = Person()
	xiaohong = Person()
	print xiaoming
	print xiaohong
	print xiaoming == xiaohong

# 创建实例属性

虽然可以通过**Person**类创建出**xiaoming**、**xiaohong**等实例，但是这些实例看上除了地址不同外，没有什么其他不同。在现实世界中，区分**xiaoming、xiaohong**要依靠他们各自的名字、性别、生日等属性。

**如何让每个实例拥有各自不同的属性？**由于Python是动态语言，对每一个实例，都可以直接给他们的属性赋值，例如，给xiaoming这个实例加上name、gender和birth属性：

	xiaoming = Person()
	xiaoming.name = 'Xiao Ming'
	xiaoming.gender = 'Male'
	xiaoming.birth = '1990-1-1'

给xiaohong加上的属性不一定要和xiaoming相同：

	xiaohong = Person()
	xiaohong.name = 'Xiao Hong'
	xiaohong.school = 'No. 1 High School'
	xiaohong.grade = 2

实例的属性可以像普通变量一样进行操作：

	xiaohong.grade = xiaohong.grade + 1

## 任务

请创建包含两个 Person 类的实例的 list，并给两个实例的 name 赋值，然后按照 name 进行排序。

sorted() 是高阶函数，接受一个比较函数。

参考代码:

	class Person(object):
	    pass
	p1 = Person()
	p1.name = 'Bart'
	
	p2 = Person()
	p2.name = 'Adam'
	
	p3 = Person()
	p3.name = 'Lisa'
	
	L1 = [p1, p2, p3]
	L2 = sorted(L1, lambda p1, p2: cmp(p1.name, p2.name))
	
	print L2[0].name
	print L2[1].name
	print L2[2].name

# 初始化实例属性

虽然我们可以自由地给一个实例绑定各种属性，但是，现实世界中，一种类型的实例应该拥有相同名字的属性。例如，Person类应该在创建的时候就拥有 name、gender 和 birth 属性，怎么办？

在定义 Person 类时，可以为Person类添加一个特殊的\_\_init\_\_()方法，当创建实例时，\_\_init\_\_()方法被自动调用，我们就能在此为每个实例都统一加上以下属性：

	class Person(object):
	    def __init__(self, name, gender, birth):
	        self.name = name
	        self.gender = gender
	        self.birth = birth

\_\_init\_\_() 方法的第一个参数必须是 self（也可以用别的名字，但建议使用习惯用法），后续参数则可以自由指定，和定义函数没有任何区别。

相应地，创建实例时，就必须要提供除 self 以外的参数：

	xiaoming = Person('Xiao Ming', 'Male', '1991-1-1')
	xiaohong = Person('Xiao Hong', 'Female', '1992-2-2')

有了\_\_init\_\_()方法，每个Person实例在创建时，都会有 name、gender 和 birth 这3个属性，并且，被赋予不同的属性值，访问属性使用.操作符：

	print xiaoming.name
	# 输出 'Xiao Ming'
	print xiaohong.birth
	# 输出 '1992-2-2'

要特别注意的是，初学者定义\_\_init\_\_()方法常常忘记了 self 参数：

	>>> class Person(object):
	...     def __init__(name, gender, birth):
	...         pass
	... 
	>>> xiaoming = Person('Xiao Ming', 'Male', '1990-1-1')
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	TypeError: __init__() takes exactly 3 arguments (4 given)

这会导致创建失败或运行不正常，因为第一个参数name被Python解释器传入了实例的引用，从而导致整个方法的调用参数位置全部没有对上。

## 任务

请定义Person类的__init__方法，除了接受 name、gender 和 birth 外，还可接受任意关键字参数，并把他们都作为属性赋值给实例。

要定义关键字参数，使用 \*\*kw；

除了可以直接使用self.name = 'xxx'设置一个属性外，还可以通过 setattr(self, 'name', 'xxx') 设置属性。

参考代码:

	class Person(object):
	    def __init__(self, name, gender, birth, **kw):
	        self.name = name
	        self.gender = gender
	        self.birth = birth
	        for k, v in kw.iteritems():
	            setattr(self, k, v)
	xiaoming = Person('Xiao Ming', 'Male', '1990-1-1', job='Student')
	print xiaoming.name
	print xiaoming.job

# 访问限制

我们可以给一个实例绑定很多属性，如果有些属性不希望被外部访问到怎么办？

Python对属性权限的控制是通过属性名来实现的，如果一个属性由**双下划线开头(\_\_)，该属性就无法被外部访问**。看例子：

	class Person(object):
	    def __init__(self, name):
	        self.name = name
	        self._title = 'Mr'
	        self.__job = 'Student'
	p = Person('Bob')
	print p.name
	# => Bob
	print p._title
	# => Mr
	print p.__job
	# => Error
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	AttributeError: 'Person' object has no attribute '__job'

可见，只有以**双下划线开头**的"\_\_job"不能直接被外部访问。

但是，如果一个属性以**"\_\_xxx\_\_"**的形式定义，那它又可以被外部访问了，以**"\_\_xxx\_\_"**定义的属性在Python的类中被称为特殊属性，有很多预定义的特殊属性可以使用，通常我们不要把普通属性用"\_\_xxx\_\_"定义。

以**单下划线开头**的属性"_xxx"虽然也可以被外部访问，但是，按照习惯，他们不应该被外部访问。

# 创建类属性

**类是模板，而实例则是根据类创建的对象。**

绑定在一个实例上的属性不会影响其他实例，但是，类本身也是一个对象，如果在类上绑定一个属性，则所有实例都可以访问类的属性，并且，所有实例访问的类属性都是同一个！也就是说，**实例属性每个实例各自拥有，互相独立，而类属性有且只有一份**。

定义类属性可以直接在 class 中定义：

	class Person(object):
	    address = 'Earth'
	    def __init__(self, name):
	        self.name = name

因为类属性是直接绑定在类上的，所以，访问类属性不需要创建实例，就可以直接访问：

		print Person.address
		# => Earth

对一个实例调用类的属性也是可以访问的，所有实例都可以访问到它所属的类的属性：

	p1 = Person('Bob')
	p2 = Person('Alice')
	print p1.address
	# => Earth
	print p2.address
	# => Earth

由于Python是动态语言，类属性也是可以动态添加和修改的：

	Person.address = 'China'
	print p1.address
	# => 'China'
	print p2.address
	# => 'China'

因为类属性只有一份，所以，当Person类的address改变时，所有实例访问到的类属性都改变了。

# 类属性和实例属性名字冲突怎么办

修改类属性会导致所有实例访问到的类属性全部都受影响，但是，如果在实例变量上修改类属性会发生什么问题呢？

	class Person(object):
	    address = 'Earth'
	    def __init__(self, name):
	        self.name = name
	
	p1 = Person('Bob')
	p2 = Person('Alice')

	print 'Person.address = ' + Person.address

	p1.address = 'China'
	print 'p1.address = ' + p1.address
	
	print 'Person.address = ' + Person.address
	print 'p2.address = ' + p2.address

结果如下：

	Person.address = Earth
	p1.address = China
	Person.address = Earth
	p2.address = Earth

我们发现，在设置了 p1.address = 'China' 后，p1访问 address 确实变成了 'China'，但是，Person.address和p2.address仍然是'Earch'，怎么回事？

原因是 p1.address = 'China'并没有改变 Person 的 address，而是给 p1这个实例绑定了实例属性address ，对p1来说，它有一个实例属性address（值是'China'），而它所属的类Person也有一个类属性address，所以:

**访问 p1.address 时，优先查找实例属性，返回'China'。**

**访问 p2.address 时，p2没有实例属性address，但是有类属性address，因此返回'Earth'。**

可见，当实例属性和类属性重名时，实例属性优先级高，它将屏蔽掉对类属性的访问。

当我们把 p1 的 address 实例属性删除后，访问 p1.address 就又返回类属性的值 'Earth'了：

	del p1.address
	print p1.address
	# => Earth

可见，千万不要在实例上修改类属性，它实际上并没有修改类属性，而是给实例绑定了一个实例属性。

# 定义实例方法

一个实例的私有属性就是以\_\_开头的属性，无法被外部访问，那这些属性定义有什么用？

虽然私有属性无法从外部访问，但是，从类的内部是可以访问的。除了可以定义实例的属性外，还可以定义实例的方法。

实例的方法就是在类中定义的函数，它的第一个参数永远是 self，指向调用该方法的实例本身，其他参数和一个普通函数是完全一样的：

	class Person(object):
	
	    def __init__(self, name):
	        self.__name = name
	
	    def get_name(self):
	        return self.__name

get_name(self) 就是一个实例方法，它的第一个参数是self。\_\_init\_\_(self, name)其实也可看做是一个特殊的实例方法。

调用实例方法必须在实例上调用：

	p1 = Person('Bob')
	print p1.get_name()  # self不需要显式传入
	# => Bob

在实例方法内部，可以访问所有实例属性，这样，如果外部需要访问私有属性，可以通过方法调用获得，这种数据封装的形式除了能保护内部数据一致性外，还可以简化外部调用的难度。

# 方法也是属性

我们在 class 中定义的实例方法其实也是属性，它实际上是一个函数对象：
	
	class Person(object):
	    def __init__(self, name, score):
	        self.name = name
	        self.score = score
	    def get_grade(self):
	        return 'A'
	
	p1 = Person('Bob', 90)
	print p1.get_grade
	# => <bound method Person.get_grade of <__main__.Person object at 0x109e58510>>
	print p1.get_grade()
	# => A

也就是说，p1.get_grade 返回的是一个函数对象，但这个函数是一个绑定到实例的函数，p1.get_grade() 才是方法调用。

因为方法也是一个属性，所以，它也可以动态地添加到实例上，只是需要用 types.MethodType() 把一个函数变为一个方法：

	import types
	def fn_get_grade(self):
	    if self.score >= 80:
	        return 'A'
	    if self.score >= 60:
	        return 'B'
	    return 'C'
	
	class Person(object):
	    def __init__(self, name, score):
	        self.name = name
	        self.score = score
	
	p1 = Person('Bob', 90)
	p1.get_grade = types.MethodType(fn_get_grade, p1, Person)
	print p1.get_grade()
	# => A
	p2 = Person('Alice', 65)
	print p2.get_grade()
	# ERROR: AttributeError: 'Person' object has no attribute 'get_grade'
	# 因为p2实例并没有绑定get_grade

给一个实例动态添加方法并不常见，直接在class中定义要更直观。

# 定义类方法

和属性类似，方法也分**实例方法**和**类方法**。

在class中定义的全部是实例方法，实例方法第一个参数 self 是实例本身。

要在class中定义类方法，需要这么写：

	class Person(object):
	    count = 0
	    @classmethod
	    def how_many(cls):
	        return cls.count
	    def __init__(self, name):
	        self.name = name
	        Person.count = Person.count + 1
	
	print Person.how_many()
	p1 = Person('Bob')
	print Person.how_many()

通过标记一个 **@classmethod**，该方法将绑定到 Person 类上，而非类的实例。类方法的第一个参数将传入类本身，通常将参数名命名为 cls，上面的 cls.count 实际上相当于 Person.count。

因为是在类上调用，而非实例上调用，因此类方法无法获得任何实例变量，只能获得类的引用。

# 参考资料

1. [廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014317848428125ae6aa24068b4c50a7e71501ab275d52000)
2. [慕课网](http://www.imooc.com/learn/317)
3. [Python官方文档](https://docs.python.org/3/)