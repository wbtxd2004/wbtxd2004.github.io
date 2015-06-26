---
layout: post
title:  神经网络学习笔记
date:   2015-06-25
categories:  ML
published: true
author: wubin

---

## 关于神经网络

## 概述

以监督学习为例，假设我们有训练样本集$$(x(^i),y(^i))$$，那么神经网络算法能够提供一种复杂且非线性的假设模型 \textstyle h_{W,b}(x) ，它具有参数 \textstyle W, b ，可以以此参数来拟合我们的数据。

$$E=mc^2$$ is a inline formula


$$ 
\begin{aligned} \dot{x} &= \sigma(y-x) \\ 
\dot{y} &= \rho x - y - xz \\ 
\dot{z} &= -\beta z + xy \end{aligned} 
$$

