---
layout: post
title:  深度学习-认识深度学习的大牛们
date:   2015-06-25
category: Deep Learning
tagline: by WuBin 武斌
tags: [DeepLearning]
published: true
author: wubin

---
简单介绍深度学习历史上的几位有名的学者以及他们之间的一些关系和轶事。

<!--more-->

>本文是根据刘小兵的帖子[“深度学习之江湖~那些大神们”][1]学习改动而来的，他讲的比较幽默风趣，而且让我获得知识，感谢他。

深度学习目前的大牛有四位：

* Geoff Hinton（杰弗里·辛顿）
	- 加入Google搞Google Brain
* Yann Lecun（燕乐存）
	- 加入Facebook任人工智能研究室主任
* Yoshua Bengio
	- 在蒙特利尔大学潜心学术界
* Andrew Ng（吴恩达）
	- 加入百度高Baidu Brain
	
四位大牛中，Yann Lecun是Hinton教授的博士后学生，Yann Lecun和Yoshua Bengio是AT&T的同时。Yoshua Bengio是Michael Jordon的博士后，Andrew Ng也是师从Michael Jordon并且是其“得意门生”。Michael Jordon目前是UC Berkey的统计学和ML的双料教授，一手开创可统计机器学习这个领域，门下高人辈出，其中最有知名度的是Ng。据说Michael Jordon当年申请Hinton的博士后被拒了，愤然出走UC Berkey,自己开宗立派，成为一代宗师。Andrew Ng在Hinton去Google之前是"Google Brain之父"，Hinton去了之后就离开Google回了stanford，然后现在再度出山，也许有其师M.J的情节在里面也许所谓一山难容二虎吧。



如果以门派论：
Jeff Hinton是深度学习的"开山祖师爷"，也是武林中的"少林派"的主持，德高望重，96年创立人工神经网络的BP算法，惊天动地，当年被给予厚望可惜ANN没有发展起来后来反被搞SVM的人压制了将近20年，据说2006以前Hinton系的人被压制到每年的NIPS ICML这样会议都发不了，因为一定会被SVM的人毙掉。终于，蛰伏良久，厚积薄发，王者归来，2006年开始推出深度神经网络，终于引领了这波浪潮。Google去年收购了2个深度学习的公司，一个是DNNResearch，只有三个员工分别是Hinton和他的两个博士生。另外一个是英国的DeepMind，创始人也是Hinton的博士生，传言花了5亿刀。

Yann Lecun可以算作DL江湖的"武当派"掌门人，因为武当派的开山鼻祖"觉远大师"也是师出少林。Yann Lecun一手创立卷积神经网络CNN，这也是目前DL在图像上边发力的必备武器。去年NIPS 2013会议上，扎克伯格突然现身，宣布Yann Lecun被他招揽到了facebook了。Yann Lecun还是纽约大学Data science center创始人和主任。

Yoshua Bengio, 从2006年开始，主要是Hinton、Yoshua、Yann Lecun开始发起的深度学习的浪潮，很多这个领域的牛paper都是出自Yoshua的手(而且是自己写)。当前学习DL有力的工具PyLearn2和Theano都是出自他们实验室。对其了解不多，只是觉得他的paper特别的厚而且自成体系。最近看到对他的采访，让他评价一下"为什么最近这些深度学习的大牛都投身工业界了?"，他的回答是："我喜欢学术界，因为我可以选择研究我喜欢的课题，我可以选择设立一个长期的目标来为之努力，我可以为全人类的福祉来奋斗而不是某一个特定公司的利益，而且我可以非常自由的公开讨论我的研究成果和进展"。不过，Yoshua会不会被某公司收揽呢，一切不好说。凡事亲力亲为，门下弟子不多，淡泊名利，从这个角度看，Yoshua Bengio是应该算作"逍遥派"的"无崖子"吧。

Andrew Ng，香港出身，中文名"吴恩达", 近几年机器学习界炙手可热的后起之秀，年龄只有38，而且是最近才结婚(在twitter上看到他show的婚纱照了)，stanford计算机副教授 & AI Lab主任。成果无数，产出惊人，比如和David Blei 以及他们的老师Michael Jordon创建的LDA（隐含狄利克雷分布简称LDA(Latent Dirichlet allocation)）就耳熟能详,此外还有Reinforcement Learning、Sparse coding、Bayesian network、NLP、Deep learning方面奇功无数(水平有限，无法概括大牛的领域)，在其主页上粗粗浏览了一下有160多篇论文，基本上统治了ICML NIPS AAAI等所有相关领域国际顶级会议和顶级期刊。前两年和D.Koller(Graphic model & Bayesian很厉害的一名女教授)合作推出了Coursera，风靡全球，让人足不出户就能聆听大师讲课。感觉Ng在学术界和工业界都很能混的开，"Google Brain之父"完了之后就是"Baidu Brain之父"，既能"出世"又能"入世"，进退自如，恢恢乎游刃有余，以stanford为据点培养了一大批博士生(比如Quoc Le现在是Google Brain的核心人员 Richard socher去年在NLP的文章也很精彩)，剑法飘逸，涉猎深广，最重要的是年轻，这点来看可以算作武林届的"令狐冲"。

那么谁是"风清扬"呢("风清扬"和"逍遥派"的关系待考证)，必然是其师Michael Jordon了，机器学习届的"泰山北斗"，就像在”风清扬“在华山一手开创剑宗一脉。Michael Jordon也是一手开创统计ML, 涵盖的领域包括： Bayesian nonparametric analysis, probabilistic graphical models, spectral methods, kernel machines and signal processing, statistical genetics, computational biology, information retrieval and natural language processing(摘自其主页介绍http://www.eecs.berkeley.edu/Faculty/Homepages/jordan.html)，正好9个领域，简直真真是"独孤九剑"了，让人叹为观止。

Jeff Dean, 人称互联网战神，Google Senior Fellow(Google工程师最高级别，这个级别就是为Jeff Dean设立的)，缔造了谷歌的很多系统和框架，极大的影响了当今互联网、大数据的技术深度和演进。其贡献包括：MapReduce BigTable的发明人(谷歌老三架马车是GFS Mapreduce Bigtable)那2篇牛paper作者，Google Adsense & Adwords第一个版本作者，Five generation谷歌网页检索系统作者、Protocal buffer作者，分布式操作系统创始人，Google News作者，Spanner作者，DistBelief作者(这个和深度学习相关), Google Translate创始人。大规模深度学习网络的第一个系统算是DistBelief, 当然对外的项目名称叫做"Google Brain". DistBelief当时用了1000台机器、16000个核做了一个深度神经网络(paper: large scale ditributed deep networks)，算是在工业界率先开启超大规模深度学习网络的先河。Jeff Dean在国内外工程师心目中简直是神一般的存在，广为流传的Jeff Dean的搞笑段子就是一个最好的说明。早期focus在编译器、并行处理、大数据架构等系统方面，近期看到的一些产出都是在机器学习+大规模系统的方面，左手机器学习，右手无出其右的架构和系统，所以从宗师级的来看，Jeff Dean应该算全真教的"王重阳"。

当然深度学习界还有一些响当当的人物，比如Li Deng、Dong Yu、Kai Yu（余凯），前两位是在微软雷蒙德研究院，和Hinton深度合作，将DL在语音识别、语音合成上的应用提上了一个新台阶，在DL的发扬光大起了至关重要的作用。Kai Yu是国人中做DL的先驱(和如上几位交集甚深，属于一个圈内的人物)，百度IDL的副厂长，一手带动深度学习在某厂的很多领域得到应用，比如：图像检索和理解、语音识别、Learning to Rank和广告里面的CTR prediction，也是国内DL的布道者，将某厂的DL的知名度和影响面成功扩大到全球领域，带动了国内DL的浪潮，可谓风头一时无两。


再说说现在深度神经网络的规模吧，最早Google的Distblief用了1000台机器、16000核处理的网络规模大概是10亿个神经元，而后Ng回了stanford之后，用了16台CPU Server，每个server插4个GPU，总共是64个GPU(但是用了一个超牛逼的交换机叫做InfiniBand)，可训练的网络规模是112亿的神经元。确实，从效率、通信、扩展性上来讲，GPU甚至是CPU+GPU是趋势，这也是Ng很快搞出一个网络规模更大、机器资源更省深度网络之后可以马上宣称"堆机器有什么用，效率才是王道"的原因(这句话是我的杜撰，但是"Deep Learning with COTS HPC Systems"确实最后讲明了这个工作的意义在于没那么多的机器照样可以做大规模的深度网络)。最近看到的消息，某厂的网络规模已经达到了200亿的节点规模(这可能也是对Ng有吸引力的地方)，他们招揽了异构的专家搞异构计算，但总之GPU还是王道。下一步呢，我自己觉得目标将会是1000亿的神经元的规模，因为深度学习的一路进展是在深度更深的背景是进行的，而且到了超大规模之后有可能能够发现一些更加不一样的东西，真能进入一片"不一样的天空"也未可知。接下来就看google、facebook还是baidu谁先到这个地步了，因为规模越大，对并行架构、优化算法(至少目前的aSgd基本不能work)提出前所未有的挑战。

PS: 这篇文章纯属八卦，一些人物细节没有详细考证，权当看个乐:)

[1]: http://www.hudongba.mobi/article/6eju