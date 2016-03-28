---
layout: post
category: Python
title:  Python学习笔记-进阶篇-[2]模块
date:   2016-03-28 12:31
tagline: by WuBin 武斌
tags: [Python]
published: true
author: 武斌

---

在计算机程序的开发过程中，随着程序代码越写越多，在一个文件里代码就会越来越长，越来越不容易维护。

为了编写可维护的代码，我们把很多函数分组，分别放到不同的文件里，这样，每个文件包含的代码就相对较少，很多编程语言都采用这种组织代码的方式。在Python中，一个.py文件就称之为一个模块（Module）。

<!--more-->

# 使用模块有什么好处？

**最大的好处是大大提高了代码的可维护性**。其次，**编写代码不必从零开始**。当一个模块编写完毕，就可以被其他地方引用。我们在编写程序的时候，也经常引用其他模块，包括Python内置的模块和来自第三方的模块。

使用模块还可以**避免函数名和变量名冲突**。相同名字的函数和变量完全可以分别存在不同的模块中，因此，我们自己在编写模块时，不必考虑名字会与其他模块冲突。但是也要注意，尽量不要与内置函数名字冲突。点[这里](http://docs.python.org/3/library/functions.html)查看Python的所有内置函数。

你也许还想到，如果不同的人编写的模块名相同怎么办？为了避免模块名冲突，Python又引入了按目录来组织模块的方法，称为包（Package）。

举个例子，一个**abc.py**的文件就是一个名字叫**abc**的模块，一个**xyz.py**的文件就是一个名字叫**xyz**的模块。

现在，假设我们的**abc**和**xyz**这两个模块名字与其他模块冲突了，于是我们可以通过包来组织模块，避免冲突。方法是选择一个顶层包名，比如**mycompany**，按照如下目录存放：

<img src="{{site.baseurl}}/images/post/2016-03-28/python_module_1.png" width="600" alt=""/>

引入了包以后，只要顶层的包名不与别人冲突，那所有模块都不会与别人冲突。现在，**abc.py**模块的名字就变成了**mycompany.abc**，类似的，**xyz.py**的模块名变成了**mycompany.xyz**。

请注意，每一个包目录下面都会有一个**\_\_init\_\_.py**的文件，这个文件是必须存在的，否则，Python就把这个目录当成普通目录，而不是一个包。**\_\_init\_\_.py**可以是空文件，也可以有Python代码，因为**\_\_init\_\_.py**本身就是一个模块，而它的模块名就是**mycompany**。

类似的，可以有多级目录，组成多级层次的包结构。比如如下的目录结构：

<img src="{{site.baseurl}}/images/post/2016-03-28/python_module_2.png" width="600" alt=""/>

文件**www.py**的模块名就是**mycompany.web.www**，两个文件**utils.py**的模块名分别是**mycompany.utils**和**mycompany.web.utils**。

自己创建模块时要注意命名，不能和Python自带的模块名称冲突。例如，系统自带了sys模块，自己的模块就不可命名为**sys.py**，否则将无法导入系统自带的sys模块。

**mycompany.web**也是一个模块，请指出该模块对应的.py文件。

# 使用示例

Python本身就内置了很多非常有用的模块，只要安装完毕，这些模块就可以立刻使用。

我们以内建的**sys**模块为例，编写一个**hello**的模块：

	#!/usr/bin/env python3
	# -*- coding: utf-8 -*-
	
	' a test module '
	
	__author__ = 'Michael Liao'
	
	import sys
	
	def test():
	    args = sys.argv
	    if len(args)==1:
	            print('Hello, world!')
	    elif len(args)==2:
	        print('Hello, %s!' % args[1])
	    else:
	        print('Too many arguments!')
	
	if __name__=='__main__':
	    test()

第1行和第2行是标准注释，第1行注释可以让这个**hello.py**文件直接在Unix/Linux/Mac上运行，第2行注释表示.py文件本身使用标准UTF-8编码；

第4行是一个字符串，表示模块的文档注释，任何模块代码的第一个字符串都被视为模块的文档注释；

第6行使用**\_\_author\_\_**变量把作者写进去，这样当你公开源代码后别人就可以瞻仰你的大名；

以上就是Python模块的标准文件模板，当然也可以全部删掉不写，但是，按标准办事肯定没错。

后面开始就是真正的代码部分。

# 导入模块

要使用一个模块，我们必须首先导入该模块。Python使用import语句导入一个模块。例如，导入系统自带的模块**math**：

	import math

你可以认为math就是一个指向已导入模块的变量，通过该变量，我们可以访问math模块中所定义的所有公开的函数、变量和类：

	>>> math.pow(2, 0.5) # pow是函数
	1.4142135623730951

	>>> math.pi # pi是变量
	3.141592653589793

如果我们只希望导入用到的math模块的某几个函数，而不是所有函数，可以用下面的语句：

	from math import pow, sin, log

这样，可以直接引用 pow, sin, log 这3个函数，但math的其他函数没有导入进来：

	>>> pow(2, 10)
	1024.0
	>>> sin(3.14)
	0.0015926529164868282

如果遇到名字冲突怎么办？比如math模块有一个log函数，logging模块也有一个log函数，如果同时使用，如何解决名字冲突？

如果使用import导入模块名，由于必须通过模块名引用函数名，因此不存在冲突：

	import math, logging
	print math.log(10)   # 调用的是math的log函数
	logging.log(10, 'something')   # 调用的是logging的log函数

如果使用 from...import 导入 log 函数，势必引起冲突。这时，可以给函数起个**“别名”**来避免冲突：

	from math import log
	from logging import log as logger   # logging的log现在变成了logger
	print log(10)   # 调用的是math的log
	logger(10, 'import from logging')   # 调用的是logging的log

# 动态导入模块

如果导入的模块不存在，Python解释器会报**ImportError**错误：

	>>> import something
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	ImportError: No module named something

有的时候，两个不同的模块提供了相同的功能，比如**StringIO**和**cStringIO**都提供了**StringIO**这个功能。

这是因为Python是动态语言，解释执行，因此Python代码运行速度慢。

如果要提高Python代码的运行速度，最简单的方法是把某些关键函数用 C 语言重写，这样就能大大提高执行速度。

同样的功能，StringIO 是纯Python代码编写的，而 cStringIO 部分函数是 C 写的，因此 cStringIO 运行速度更快。

利用ImportError错误，我们经常在Python中动态导入模块：

	try:
	    from cStringIO import StringIO
	except ImportError:
	    from StringIO import StringIO

上述代码先尝试从cStringIO导入，如果失败了（比如cStringIO没有被安装），再尝试从StringIO导入。这样，如果cStringIO模块存在，则我们将获得更快的运行速度，如果cStringIO不存在，则顶多代码运行速度会变慢，但不会影响代码的正常执行。

**try**的作用是捕获错误，并在捕获到指定错误时执行**except**语句。

# 使用\_\_future\_\_

Python的新版本会引入新的功能，但是，实际上这些功能在上一个老版本中就已经存在了。要“试用”某一新的特性，就可以通过导入\_\_future\_\_模块的某些功能来实现。

例如，Python 2.7的整数除法运算结果仍是整数：

	>>> 10 / 3
	3

但是，Python 3.x已经改进了整数的除法运算，“/”除将得到浮点数，“//”除才仍是整数：

	>>> 10 / 3
	3.3333333333333335
	>>> 10 // 3
	3

要在Python 2.7中引入3.x的除法规则，导入\_\_future\_\_的division：

	>>> from __future__ import division
	>>> print 10 / 3
	3.3333333333333335

当新版本的一个特性与旧版本不兼容时，该特性将会在旧版本中添加到\_\_future\_\_中，以便旧的代码能在旧版本中测试新特性。

# 安装第三方模块

在Python中，安装第三方模块，是通过包管理工具pip完成的。

如果你正在使用Mac或Linux，安装pip本身这个步骤就可以跳过了。

如果你正在使用Windows，请参考[安装Python](http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014316090478912dab2a3a9e8f4ed49d28854b292f85bb000)一节的内容，确保安装时勾选了pip和Add python.exe to Path。

在命令提示符窗口下尝试运行pip，如果Windows提示未找到命令，可以重新运行安装程序添加pip。

注意：Mac或Linux上有可能并存Python 3.x和Python 2.x，因此对应的pip命令是pip3。

现在，让我们来安装一个第三方库——Python Imaging Library，这是Python下非常强大的处理图像的工具库。不过，PIL目前只支持到Python 2.7，并且有年头没有更新了，因此，基于PIL的Pillow项目开发非常活跃，并且支持最新的Python 3。

一般来说，第三方库都会在Python官方的[pypi.python.org](https://pypi.python.org/)网站注册，要安装一个第三方库，必须先知道该库的名称，可以在官网或者pypi上搜索，比如Pillow的名称叫Pillow，因此，安装Pillow的命令就是：

	pip install Pillow

耐心等待下载并安装后，就可以使用Pillow了。

有了Pillow，处理图片易如反掌。随便找个图片生成缩略图：

	>>> from PIL import Image
	>>> im = Image.open('test.png')
	>>> print(im.format, im.size, im.mode)
	PNG (400, 300) RGB
	>>> im.thumbnail((200, 100))
	>>> im.save('thumb.jpg', 'JPEG')

其他常用的第三方库还有MySQL的驱动:**mysql-connector-python**，用于科学计算的NumPy库:**numpy**，用于生成文本的模板工具**Jinja2**等等。

模块搜索路径

当我们试图加载一个模块时，Python会在指定的路径下搜索对应的.py文件，如果找不到，就会报错：

	>>> import mymodule
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	ImportError: No module named mymodule

默认情况下，Python解释器会搜索当前目录、所有已安装的内置模块和第三方模块，搜索路径存放在sys模块的path变量中：

	>>> import sys
	>>> sys.path
	['', '/Library/Frameworks/Python.framework/Versions/3.4/lib/python34.zip', '/Library/Frameworks/Python.framework/Versions/3.4/lib/python3.4', '/Library/Frameworks/Python.framework/Versions/3.4/lib/python3.4/plat-darwin', '/Library/Frameworks/Python.framework/Versions/3.4/lib/python3.4/lib-dynload', '/Library/Frameworks/Python.framework/Versions/3.4/lib/python3.4/site-packages']

如果我们要添加自己的搜索目录，有两种方法：

一是直接修改sys.path，添加要搜索的目录：

	>>> import sys
	>>> sys.path.append('/Users/michael/my_py_scripts')

这种方法是在运行时修改，运行结束后失效。

第二种方法是设置环境变量PYTHONPATH，该环境变量的内容会被自动添加到模块搜索路径中。设置方式与设置Path环境变量类似。注意只需要添加你自己的搜索路径，Python自己本身的搜索路径不受影响。

# 参考资料

1. [廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014317848428125ae6aa24068b4c50a7e71501ab275d52000)
2. [慕课网](http://www.imooc.com/learn/317)
3. [Python官方文档](https://docs.python.org/3/)