---
layout: post
category: Python
title:  Python学习笔记-基础篇-[1]Python简介
date:   2016-03-22 09:37:05
tagline: by WuBin 武斌
tags: [Python]
published: true
author: 武斌

---

本篇是Python的基本介绍，主要包括什么是Python，Python能干什么，使用Python有什么优势和劣势。**注意：本系列教程都是针对Python3的版本**

<!--more-->

# 什么是Python(维基百科)
Python是著名的“龟叔”Guido van Rossum在1989年圣诞节期间，为了打发无聊的圣诞节而编写的一个编程语言。

## 定义
Python（英国发音：/ˈpaɪθən/ 美国发音：/ˈpaɪθɑːn/），是一种面向对象、直译式的计算机程序语言，具有近二十年的发展历史。它包含了一组功能完备的标准库，能够轻松完成很多常见的任务。它的语法简单，与其它大多数程序设计语言使用大括号不一样，它使用缩进来定义语句块。

与Scheme、Ruby、Perl、Tcl等动态语言一样，Python具备垃圾回收功能，能够自动管理内存使用。它经常被当作脚本语言用于处理系统管理任务和网络程序编写，然而它也非常适合完成各种高级任务。Python虚拟机本身几乎可以在所有的作业系统中运行。使用一些诸如py2exe、PyPy、PyInstaller之类的工具可以将Python源代码转换成可以脱离Python解释器运行的程序。

Python的官方解释器是CPython，该解释器用C语言编写，是一个由社区驱动的自由软件，目前由Python软件基金会管理。

Python支持命令式程序设计、面向对象程序设计、函数式编程、面向侧面的程序设计、泛型编程多种编程范式。

## 实现
Python是一门跨平台的脚本语言，Python规定了一个Python语法规则，根据该规则可编写Python解释器。

- CPython，官方的解释器。需要区别于其他解释器的时候才以CPython称呼。这是最常用的Python版本。
- Jython（原名JPython；Java语言实现的Python，现已正式发布）。Jython可以直接调用Java的各种函数库。
- PyPy（使用Python语言写的Python）
- IronPython（面向.NET和ECMA CLI的Python实现）。IronPython能够直接调用.net平台的各种函数库。可以将Python程序编译成.net程序。
- ZhPy（周蟒，支持使用繁/简中文语句编写程序的Python语言）

## 现状
现在，全世界差不多有600多种编程语言，但流行的编程语言也就那么20来种。如果你听说过TIOBE排行榜，你就能知道编程语言的大致流行程度。这是最近10年最常用的10种编程语言的变化图：

<img src="{{site.baseurl}}/images/post/2016-03-24/python-tiobe-1.jpg" width="600" alt=""/>

最新的TIOBE编程语言排行:

<img src="{{site.baseurl}}/images/post/2016-03-24/python-tiobe-2.jpg" width="600" alt=""/>

总的来说，这几种编程语言各有千秋。C语言是可以用来编写操作系统的贴近硬件的语言，所以，C语言适合开发那些追求运行速度、充分发挥硬件性能的程序。而Python是用来编写应用程序的高级编程语言。

当你用一种语言开始作真正的软件开发时，你除了编写代码外，还需要很多基本的已经写好的现成的东西，来帮助你加快开发进度。比如说，要编写一个电子邮件客户端，如果先从最底层开始编写网络协议相关的代码，那估计一年半载也开发不出来。高级编程语言通常都会提供一个比较完善的基础代码库，让你能直接调用，比如，针对电子邮件协议的SMTP库，针对桌面环境的GUI库，在这些已有的代码库的基础上开发，一个电子邮件客户端几天就能开发出来。

# Python能干什么

首选是网络应用，包括网站、后台服务等等；

其次是许多日常需要的小工具，包括系统管理员需要的脚本任务等等；

另外就是把其他语言开发的程序再包装起来，方便使用。
##Web程序
Python经常被用于Web开发。比如，通过mod_wsgi模块，Apache可以运行用Python编写的Web程序。使用Python语言编写的Gunicorn作为Web服务器，也能够运行Python语言编写的Web程序。Python定义了WSGI标准应用接口来协调Http服务器与基于Python的Web程序之间的沟通。一些Web框架，如Django、Pyramid、TurboGears、Tornado、web2py、Zope、Flask等，可以让程序员轻松地开发和管理复杂的Web程序。

Python对于各种网络协议的支持很完善，因此经常被用于编写服务器软件、网络蠕虫。第三方库Twisted支持异步在线编写程序和多数标准的网络协议（包含客户端和服务器），并且提供了多种工具，被广泛用于编写高性能的服务器软件。另有gevent这个流行的第三方库，同样能够支持高性能高并发的网络开发。

##GUI开发
Python本身包含的Tkinter库能够支持简单的GUI开发。但是越来越多的Python程序员选择wxPython或者PyQt等GUI包来开发跨平台的桌面软件。使用它们开发的桌面软件运行速度快，与用户的桌面环境相契合。通过PyInstaller还能将程序发布为独立的安装程序包。

##操作系统
在很多操作系统里，Python是标准的系统组件。大多数Linux发行版以及NetBSD、OpenBSD和Mac OS X都集成了Python，可以在终端机下直接运行Python。有一些Linux发行版的安装器使用Python语言编写，比如Ubuntu的Ubiquity安装器、Red Hat Linux和Fedora的Anaconda安装器。Gentoo Linux使用Python来编写它的Portage软件包管理系统。Python标准库包含了多个调用作业系统功能的库。通过pywin32这个第三方软件包，Python能够访问Windows的COM服务及其它Windows API。使用IronPython，Python程序能够直接调用.Net Framework。

##其他
NumPy、SciPy、Matplotlib可以让Python程序员编写科学计算程序。有些公司会使用Scons代替make构建C++程序。

很多游戏使用C++编写图形显示等高性能模块，而使用Python或者Lua编写游戏的逻辑、服务器。相较于Python，Lua的功能更简单、体积更小；而Python则支持更多的特性和数据类型。很多游戏，如EVE Online使用Python来处理游戏中繁多的逻辑。

YouTube、Google、Yahoo!、NASA都在内部大量地使用Python。OLPC的作业系统Sugar项目的大多数软件都是使用Python编写。

## 使用Python编写的著名应用
- Reddit - 社交分享网站
- Dropbox - 文件分享服务
- 豆瓣网 - 图书、唱片、电影等文化产品的资料数据库网站
- Django - 鼓励快速开发的Web应用框架
- Pylons - Web应用框架
- Zope - 应用服务器
- Plone - 内容管理系统
- TurboGears - 另一个Web应用快速开发框架
- Twisted - Python的网络应用程序框架
- Fabric - 用于管理成百上千台Linux主机的程序库
- Python Wikipedia Robot Framework - MediaWiki的机器人程序
- MoinMoinWiki - Python写成的Wiki程序
- Trac - 使用Python编写的BUG管理系统
- Mailman - 使用Python编写的邮件列表软件
- Mezzanine - 基于Django编写的内容管理系统系统
- flask - Python微Web框架
- Webpy - Python微Web框架
- Bottle - Python微Web框架
- EVE - 网络游戏EVE大量使用Python进行开发
- Blender - 使用Python作为建模工具与GUI语言的开源3D绘图软件
- Inkscape - 一个开源的SVG矢量图形编辑器。
- 知乎 - 一个问答网站
- 果壳 - 一个泛科技主题网站

# Python的优点
Python就为我们提供了非常完善的基础代码库，覆盖了网络、文件、GUI、数据库、文本等大量内容，被形象地称作“内置电池（batteries included）”。用Python开发，许多功能不必从零编写，直接使用现成的即可。

除了内置的库外，Python还有大量的第三方库，也就是别人开发的，供你直接使用的东西。当然，如果你开发的代码通过很好的封装，也可以作为第三方库给别人使用。

许多大型网站就是用Python开发的，例如YouTube、Instagram，还有国内的豆瓣。很多大公司，包括Google、Yahoo等，甚至NASA（美国航空航天局）都大量地使用Python。

龟叔给Python的定位是“优雅”、“明确”、“简单”，所以Python程序看上去总是简单易懂，初学者学Python，不但入门容易，而且将来深入下去，可以编写那些非常非常复杂的程序。

总的来说，Python的哲学就是简单优雅，尽量写容易看明白的代码，尽量写少的代码。如果一个资深程序员向你炫耀他写的晦涩难懂、动不动就几万行的代码，你可以尽情地嘲笑他。

# Python的缺点
任何编程语言都有缺点，Python也不例外。优点说过了，那Python有哪些缺点呢？
## 缺点一
第一个缺点就是运行速度慢，和C程序相比非常慢，因为Python是解释型语言，你的代码在执行时会一行一行地翻译成CPU能理解的机器码，这个翻译过程非常耗时，所以很慢。而C程序是运行前直接编译成CPU能执行的机器码，所以非常快。

但是大量的应用程序不需要这么快的运行速度，因为用户根本感觉不出来。例如开发一个下载MP3的网络应用程序，C程序的运行时间需要0.001秒，而Python程序的运行时间需要0.1秒，慢了100倍，但由于网络更慢，需要等待1秒，你想，用户能感觉到1.001秒和1.1秒的区别吗？这就好比F1赛车和普通的出租车在北京三环路上行驶的道理一样，虽然F1赛车理论时速高达400公里，但由于三环路堵车的时速只有20公里，因此，作为乘客，你感觉的时速永远是20公里。

## 缺点二

第二个缺点就是代码不能加密。如果要发布你的Python程序，实际上就是发布源代码，这一点跟C语言不同，C语言不用发布源代码，只需要把编译后的机器码（也就是你在Windows上常见的xxx.exe文件）发布出去。要从机器码反推出C代码是不可能的，所以，凡是编译型的语言，都没有这个问题，而解释型的语言，则必须把源码发布出去。

这个缺点仅限于你要编写的软件需要卖给别人挣钱的时候。好消息是目前的互联网时代，靠卖软件授权的商业模式越来越少了，靠网站和移动应用卖服务的模式越来越多了，后一种模式不需要把源码给别人。

再说了，现在如火如荼的开源运动和互联网自由开放的精神是一致的，互联网上有无数非常优秀的像Linux一样的开源代码，我们千万不要高估自己写的代码真的有非常大的“商业价值”。那些大公司的代码不愿意开放的更重要的原因是代码写得太烂了，一旦开源，就没人敢用他们的产品了。
## 其它
当然，Python还有其他若干小缺点，请自行忽略，就不一一列举了。


# 为什么选择Python

如果你是个学生,你应该会C，C++和Java。还会一些VB，或C#/.NET。多少你还可能开发过一些Web网页，你知道一些HTML，CSS和JavaScript知识。总体上说，我们很难发现会有学生显露出掌握超出这几种语言范围外的语言的才能。这真让人遗憾，因为还有很多种编程语言，它们能让你成为一个更好的程序员。

那么为什么你一定要学习Python语言呢？

1. 跟**C/C++/Java**相比 — Python能让你用少的多的多的代码写出相同的程序。有人计算过，Python写出的程序的代码行数只相当于相对应的Java代码的行数的五分之一。如果没有绝对的必要，为什么要花这么多时间写出这么多的代码呢？而且，有人说，一个优秀的程序员能维护的代码量最多是2万行。这不区分用的语言究竟是汇编，C还是Python /PHP/Lisp。所以，如果你用Python写，你一个人干的，不管是干什么，如果换用Java/C/C++，那都需要一个5人的小团队来干。
2. 跟**VB/PHP**比较 — 跟PHP/VB相比，Python是一种从设计上讲比它们好的不知多少倍的语言。PHP和VB分别是在开发网站和桌面应用程序上非常流行的语言。它们流行的原因是非常的易学。不懂计算机的人也很容易的上手。如果你用这些语言开发过大型的项目，你就会发现这些语言的设计是如此的糟糕。是朋友，他就不会劝你使用PHP/VB。
3. 跟**Lisp/Scala/Haskell/Closure/Erlang**相比 — Python 跟它们比起来显得相当的“主流”。确实，这些语言每种都有其很酷的特征，对于高级编程人员，了解这些语言能给他们对编程的思考带来实际的提升。但这些应该在你以后的职业生涯中才去决定学哪一两种。对于现在，Python是在语言功能和实际运用之间平衡后的更好的选择。
4. 跟Perl相比 — Python受恩于Perl，在Python异军突起前，Perl是最好、最大的一种动态语言。但现在，Perl已是明日黄花，越来越多的人转向Python。我感觉Perl的面向对象机制有点做作，很不好用。通常认为，Perl一种比较难学的语言，因为它提供你了太多不同的方法去完成同一个任务，它的语法有点像密码，非常不直观 — 除非你对它掌握的非常好。总之，我感觉Perl是一种对于学生来说不是很合适的语言—除非你有特殊的理由去学它(例如，你有很多正则表达式要处理，这是Perl的闪光点)。
5. 跟**sh/sed/awk/bash**相比 — 如果你使用Linux/Unix，你可能需要做一些shell编程，甚至会编写一些不小的程序。但是，对于这些语言，一旦程序达到一定的行数，事情就会开始变得让你痛苦不堪，你最好是用Python去做这些事情。当然，做这种事情，Perl是最好的选择，Python排第二。

你可以在Google上搜一下“为什么X比Y好” — 其中把X换成Python，把Y换成另外一种语言 — 你就会发现，有无数的文章来说明它们为什么这么好。

**选择Python能让你在开发项目的过程中节省一半的时间(除非你要开发的是移动应用，这样你必须要使用Java或Objective-C)**

下面是[xkcd](http://xkcd.com/353/)上的一幅漫画，告诉你掌握Python后你会变得多么的强大：

<img src="{{site.baseurl}}/images/post/2016-03-24/python-xkcd.png" width="600" alt=""/>

## 学习资源
[谷歌的Python课程](http://code.google.com/edu/languages/google-python-class/)，学习Python的好资源。


# 参考文档
1. [廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014317848428125ae6aa24068b4c50a7e71501ab275d52000)
2. [慕课网](http://www.imooc.com/learn/317)
3. [Python官方文档](https://docs.python.org/3/)
4. [维基百科](https://zh.wikipedia.org/wiki/Python)
5. [每个程序员都应该学会使用Python](http://www.vaikan.com/why-every-programmer-should-learn-python-or-ruby/)