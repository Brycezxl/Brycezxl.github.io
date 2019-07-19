---
title: Aspect Extraction
categories:
 - ABSA
tags:
 - ABSA
---



几篇SOTA论文笔记

<br />

<!--more-->



### Unified

A Unified Model for Opinion Target Extraction and Target Sentiment Prediction（AAAI 2018）

![1](/pictures/aspect1.png)

#### 贡献

1. 将TBSA的提取和分析放到一个模型里
2. LSTM后接三个人工特征

#### 概括

##### 1. 第一层lstm预测opinion边界（开头、中间、结尾）辅助第二层，第二层lstm分析情感，进一步预测

##### 2. 在第二层的输出上加上人工特征

1. Boundary Guidance 根据第一层LSTM的边界引导第二层LSTM（有必要吗？）
2. Sentiment Consistency 类似GRU
3. Opinion Enhanced 根据意见目标和意见词总是一起出现的特点，提高质量



-------



### OpinionSummary

Aspect Term Extraction with History Attention and Selective Transformation（IJCAI 2018）

![1](/pictures/aspect2.png)

#### 贡献

1. 利用opinion summary辅助提取aspect term（两者总是一起出现）
2. 提出aspect prediction history：一、前一时刻对当前时刻有帮助。二、已经提取出的aspect有助于识别之后的不常见aspect

#### 概括

##### 1. 双向LSTM提取初步token表示

##### 2. Truncated History-Attention提取Aspect History

   

   ![1](/pictures/aspect3.png)

   ![1](/pictures/aspect4.png)

   

   t是当前time step, i是前N个隐藏层.这一步就是普通的attn,获得当前的ht与之前的hi,summary的联系.

h也就是lstm对aspect的表示.提升正确率也能获得aspect之间的联系.但是不是很理解这样的求和attn方法.

   

   ![1](/pictures/aspect5.png)

   

   为了利用之前的检测,也就是ht,加入了残差.最终的参考历史的aspect表示就是ht加上attn

   

##### 3. Selective Transformation Network 获得opinion

   ![1](/pictures/aspect6.png)

   想法就是先用历史的aspect过滤一遍,再进行最后的组合(为什么不在最后一起操作?).

先用lstm产生hio,然后也是利用残差,hio+hio与历史aspect过一次fc的结果,这就是对杂音的过滤,再把它attn以后和历史apect线性操作,生成最后的opinion结果.

#####  4. 最后opinion和aspect拼起来过一层fc



-------



### DE-CNN

Double Embeddings and CNN-based Sequence Labeling for Aspect Extraction (ACL 2018)

![1](/pictures/aspect7.png)

#### 贡献

1. 简单的CNN
2. open-domain和specific的embedding二选一