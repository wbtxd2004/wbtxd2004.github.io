---
layout: post
title:  神经网络学习笔记
category: Machine Learning
date:   2015-06-26
tagline: by WuBin 武斌
tags: [DeepLearning, Machine Learning, Neural Network]
published: true
author: wubin

---
关于神经网络的学习，不定期更新中。

<!--more-->

## 关于神经网络

## 概述

以监督学习为例，假设我们有训练样本集$$(x(^i),y(^i))$$，那么神经网络算法能够提供一种复杂且非线性的假设模型$$h_{W,b}(x)$$，它具有参数$$ W, b $$，可以以此参数来拟合我们的数据。

为了描述神经网络，我们先从最简单的神经网络讲起，这个神经网络仅由一个“神经元”构成，以下即是这个“神经元”的图示：

<img src="{{site.baseurl}}/images/post/2015-06-02/PythonOpenCV.gif" width="600"/>


