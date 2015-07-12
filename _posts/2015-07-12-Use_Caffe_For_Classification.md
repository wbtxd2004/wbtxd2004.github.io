---
layout: post
category: Deep Learning
title:  使用Caffe进行图像分类的流程
date:   2015-07-12 22:26:05
tagline: by WuBin 武斌
tags: [DeepLearning, Image Classification, caffe]
author: wubin
published: true
---
本文主要介绍了通过caffe以及CIFAR－10数据集进行图像分类的过程。
<!--more-->
## 创建训练集

	在测试阶段我们选择的训练集是CIFAR－10，共有60000张图像，其中有10000张为测试图像，这个分为10类,详细的介绍在戴嘉伦的github上有详细的介绍。
	其实在拿到一个数据集后，一般是包含两部分的，一是图像本身，二是图像中包含label数据。有了训练集以后我们要把它转换成Caffe可以读取的数据格式，主要有Lmdb和LevelDB两种形式。
	先说LevelDB，他是一个由Google实现的非常高效的Key-Value数据库，支持十亿级别的数据量。主要归功于LSM算法使得它在非常大的数量级别下还有非常高的性能。
	LMDB的全称是Lightning Memory-Mapped Database，闪电般的内存映射数据库。它文件结构简单，一个文件夹，里面一个数据文件，一个锁文件。数据随意复制，随意传输。它的访问简单，不需要运行单独的数据库管理进程，只要在访问数据的代码里引用LMDB库，访问时给文件路径即可。
	它们都是键/值对（Key/Value Pair）嵌入式数据库管理系统编程库。虽然lmdb的内存消耗是leveldb的1.1倍，但是lmdb的速度比leveldb快10%至15%，更重要的是lmdb允许多种训练模型同时读取同一组数据集。因此lmdb取代了leveldb成为Caffe默认的数据集生成格式。
	对于CIFAR－10数据集，Caffe通过其example下的“create_cifar10.sh”脚本对data目录下的二进制的Cifar数据集转换成lmdb格式。其中主要用到了“convert_cifar_data.cpp”这个程序，这个程序目前还没有看明白。
	当然如果数据集是自己的数据集的话，可以通过caffe_root/examples/imagenet下的“create_imagenet.sh”脚本将自有的图片和Label文件转化为lmdb格式，不过这个目前还在测试中。
	

## 对训练集进行训练

	在选定CIFAR—10作为训练集的情况下， 
## 使用训练结果对测试集进行分类
##	 对分类结果进行评价


## 参考资料

1. [ImageNet tutorial](http://caffe.berkeleyvision.org/gathered/examples/imagenet.html)
2. [CIFAR-10 tutorial](http://caffe.berkeleyvision.org/gathered/examples/cpp_classification.html)
3. [使用Caffe对图片进行训练并分类的简单流程](http://blog.csdn.net/deeplearninglc007/article/details/40086503)
4. [Caffe提取任意层特征并进行可视化](http://www.cnblogs.com/platero/p/3967208.html)