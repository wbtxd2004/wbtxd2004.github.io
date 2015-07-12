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

对于CIFAR－10数据集，Caffe通过其example下的“create\_cifar10.sh”脚本对data目录下的二进制的Cifar数据集转换成lmdb格式。其中主要用到了“convert\_cifar\_data.cpp”这个程序，这个程序目前还没有看明白。

当然如果数据集是自己的数据集的话，可以通过caffe_root/examples/imagenet下的“create\_imagenet.sh”脚本将自有的图片和Label文件转化为lmdb格式，不过这个目前还在测试中。
	

## 对训练集进行训练


在选定CIFAR—10作为训练集的情况下， 可以直接使用Caffe提供的model进行训练，CIFAR-10 模型是一个由卷积层、池层、修正线性单元和一个在最顶层的局部对比度归一化的线性分类器组成的卷积神经网络。并且这个模型已经在 CAFFE_ROOT/examples/cifar10下的“cifar10\_quick\_train\_test.prototxt”和“cifar10\_full\_train\_test.prototxt”给定了。

在训练的过程中，只要使用对应的model对测试集进行训练就好了。

    cd $CAFFE_ROOT
    ./examples/cifar10/train_full.sh

通过阅读“train_full.sh”，可以知道脚本主要使用了

    caffe train --solver=examples/cifar10/cifar10_full_solver.prototxt

这个命令。
这个*.solver_prototxt的内容是：

    # reduce learning rate after 120 epochs (60000 iters) by factor 0f 10                                               
    # then another factor of 10 after 10 more epochs (5000 iters)
    # The train/test net protocol buffer definition
    net: "examples/cifar10/cifar10_full_train_test.prototxt"
    # test_iter specifies how many forward passes the test should carry out.
    # In the case of CIFAR10, we have test batch size 100 and 100 test iterations,
    # covering the full 10,000 testing images.
    test_iter: 100
    # Carry out testing every 1000 training iterations.
    test_interval: 1000
    # The base learning rate, momentum and the weight decay of the network.
    base_lr: 0.001
    momentum: 0.9
    weight_decay: 0.004
    # The learning rate policy
    lr_policy: "fixed"
    # Display every 200 iterations
    display: 200
    # The maximum number of iterations
    max_iter: 60000
    # snapshot intermediate results
    snapshot: 10000
    snapshot_prefix: "examples/cifar10/cifar10_full"
    # solver mode: CPU or GPU
    solver_mode: GPU

可以看出来这是一个网络的配置文件，首先设定了训练和测试的网络结构“examples/cifar10/cifar10\_full\_train\_test.prototxt”,其次设定了迭代次数、学习率、动量和权重衰减值等。
对于训练网络的设定，可以看之前在github上的总结。

训练完成后，会在训练的目录下生成一个caffemodel后缀文件和solverstate后缀的文件。主要使用的是caffemodel文件，它就是训练好的模型，而solverstate文件记录了所有快照/恢复必需的信息，包括参数、历史等等。
## 使用训练结果对测试集进行分类

训练好模型后，下一步就是使用训练好的模型对图像进行分类了，在这里主要有两种方式，一种是基于python的，一种是C++的，我现在正在看这两部分的代码，有点复杂。

1. 使用caffe提供的classify.py代码对图像进行分类。这一部分主要是参照参考资料5以及自己看代码。
 * 修改参数
  
  将参数中的"--model_def"的值改为网络结构的prototxt，例如我是这样改的：
  
    parser.add_argument(
        "--model_def",
        default=os.path.join(pycaffe_dir,
                "../../examples/cifar10/cifar10_full_train_test.prototxt"),
        help="Model definition file."
    )
  
  将参数pretrained_model改为之前训练好的参数文件，例如我是这样改的：
  
    parser.add_argument(
        "--pretrained_model",
        default=os.path.join(pycaffe_dir,
                "../../examples/cifar10/cifar10_full_iter_70000.caffemodel"),
        help="Trained model weights file."
    )

  
 * 执行命令
 
 进入终端，切换到caffe的跟目录，执行命令。
 
    cd $CAFFE_ROOT
 
    python examples/cifar10/python/classifytest.py\
    examples/cifar10/classify/cat.jpg\
    output
 
 程序运行结束后，会生成output.npy文件，里面是分类结果。但是现在这个功能不完善，只是提供一个正确率，所以需要进一步的改进。

2. 使用caffe提供的classification.cpp程序对图像进行分类，这一部分主要参照参考资料6，这一部分没有测试，正在看代码，下一步就是测试。
 
 在参考资料中，用到的代码如下：
	
    ./build/examples/cpp_classification/classification.bin \ models/bvlc_reference_caffenet/deploy.prototxt \ models/bvlc_reference_caffenet/bvlc_reference_caffenet.caffemodel \ data/ilsvrc12/imagenet_mean.binaryproto \ data/ilsvrc12/synset_words.txt \ examples/images/cat.jpg

 
 可以借鉴。
 
3. 使用自己设计的代码进行分类，这一部分可以参照参考资料3，我现在还没有详细的做，先把1和2看明白了再说吧。

之前使用python的方式（第一种），参照参考资料5对测试图片进行了分类，不过效果很不明显，分类成功率只有17%，目前正处在一个纠错的过程中。分类结果如图所示：
<img src="{{site.baseurl}}/images/post/2015-07-12/caffe_classification.png" width="600"/>

##	 对分类结果进行优化

可以通过很多方式对分类结果进行优化，现在还没有做，先mark下，等有了这部分的工作会再补充上。


## 参考资料

1. [ImageNet tutorial](http://caffe.berkeleyvision.org/gathered/examples/imagenet.html)
2. [CIFAR-10 tutorial](http://caffe.berkeleyvision.org/gathered/examples/cpp_classification.html)
3. [使用Caffe对图片进行训练并分类的简单流程](http://blog.csdn.net/deeplearninglc007/article/details/40086503)
4. [Caffe提取任意层特征并进行可视化](http://www.cnblogs.com/platero/p/3967208.html)
5. [利用训练好的Caffe网络得到输入图像的分类](http://blog.csdn.net/deeplearninglc007/article/details/41283985)
6. [Classifying ImageNet: using the C++ API](http://caffe.berkeleyvision.org/gathered/examples/cpp_classification.html)