---
title: Ng Machine Learning
description: 吴恩达coursera
tags:
 - 新手村
---
吴恩达coursera
{:.success}

<!--more-->

***

## SVM

![1](/pictures/svm.png)

![1](/pictures/svm_kernel.png)

![1](/pictures/svm_landmark.png)

![1](/pictures/svm_params.png)

![1](/pictures/svm_process.png)

***

## Evalueate

提高正确率方法：

* 更多数据
* 更少特征
* 更多特征
* 增加多项式
* 减小lambda
* 增大lambda



diagnostic:

选择模型：

* 60% 训练集 20%交叉测试集  20% 测试集 
* 通过训练集获得theta，用交叉测试集选择j最小的模型，用测试集测试模型泛化

bias（underfit）：J-train和J-cv都大

variance（overfit）：j-train小  j-cv>>j-train


lambda= 0,  0.02, 0.04, 0.08 ....10 看哪个jcv小 用jcv去测试jtest

![1](/pictures/bias.png)

![2](/pictures/variance.png)

