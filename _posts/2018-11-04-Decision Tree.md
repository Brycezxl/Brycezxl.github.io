---
layout : article
title  : Decision Tree
key    : 20181104
tag    : 入门
sidebar:
  nav  : docs-en   
title: Decision Tree
description: Decision Tree
tags:
 - 新手村
 - 机器学习
---

#### Introduce 3 algorithms of Decision Tree.
<br />

<!--more-->

***
## ID3

算法的过程为：

1. 初始化信息增益的阈值ϵϵ
2. 判断样本是否为同一类输出DiDi，如果是则返回单节点树T。标记类别为Di
3. 判断特征是否为空，如果是则返回单节点树T，标记类别为样本中输出类别D实例数最多的类别。
4. 计算A中的各个特征（一共n个）对输出D的信息增益，选择信息增益最大的特征Ag

$ E(S)=−\sum_{i=1}^Np(x_i)log_2(p(x_i)) $
      
$ E_A(S)=-\sum_{j=1}^m\frac {S_j}{S}E(S_j) $
      
$ InfoGain(S,A)=E(S)−E_A(S) $

5. 如果AgAg的信息增益小于阈值ϵϵ，则返回单节点树T，标记类别为样本中输出类别D实例数最多的类别。
6. 否则，按特征AgAg的不同取值AgiAgi将对应l的样本输出D分成不同的类别DiDi。每个类别产生一个子节点。对应特征值为AgiAgi。返回增加了节点的数T。
7. 对于所有的子节点，令D=Di,A=A−{Ag}D=Di,A=A−{Ag}递归调用2-6步，得到子树TiTi并返回。

缺点：　
* ID3没有考虑连续特征，比如长度，密度都是连续值，无法在ID3运用。这大大限制了ID3的用途。
* ID3采用信息增益大的特征优先建立决策树的节点。很快就被人发现，在相同条件下，取值比较多的特征比取值少的特征信息增益大。比如一个变量有2个值，各为1/2，另一个变量为3个值，各为1/3，其实他们都是完全不确定的变量，但是取3个值的比取2个值的信息增益大。如果校正这个问题呢？
* ID3算法对于缺失值的情况没有做考虑
* 没有考虑过拟合的问题

***

## C4.5

### 信息增益率：

$ Splitinfo_A(S)=-\sum_{j=1}^m\frac {S_j}{S}log(\frac {S_j}{S}) $

$ InfoGain(S,A)=E(S)−E_A(S) $

$ InfoGainRation(S,A)= \frac {InfoGain(S,A)}{Splitinfo_A(S)} $

训练数据集S通过属性A的属性值划分为m个子数据集，`Sj`表示第j个子数据集中样本数量，`S`表示划分之前数据集中样本总数量。 

### 连续型属性的离散化处理 

  将属性A的N个属性值按照升序排列；通过二分法将属性A的所有属性值分成两部分（共有N-1种划分方法，二分的阈值为相邻两个属性值的中间值）；计算每种划分方法对应的信息增益，选取信息增益最大的划分方法的阈值作为属性A二分的阈值。

### 剪枝法 

PEP(Pessimistic Error Pruning)

预剪枝: 在构建决策树的过程中，提前终止决策树的生长，从而避免过多的节点产生。预剪枝方法虽然简单但实用性不强，因为很难精确的判断何时终止树的生长。

后剪枝: 在决策树构建完成之后，对那些置信度不达标的节点子树用叶子结点代替，该叶子结点的类标号用该节点子树中频率最高的类标记。后剪枝方法又分为两种，一类是把训练数据集分成树的生长集和剪枝集；另一类算法则是使用同一数据集进行决策树生长和剪枝。

***

## CART

Classification And Regression Tree

### Gini算法

  分类过程中，假设有K个类，可以得到样本集合D的基尼指数，其中Ck表示数据集D中属于第k类的样本子集

$ Gini(A)=1-\sum_{k=1}^K{(\frac {C_k}{D})}^2 $


　　如果数据集D根据特征A在某一取值a上进行分割，得到D1,D2两部分后，那么在特征A下集合D的基尼系数如下所示。其中基尼系数Gini(D)表示集合D的不确定性，基尼系数Gini(D,A)表示A=a分割后集合D的不确定性。基尼指数越大，样本集合的不确定性越大。对于训练集S，计算所有属性的最优二分方案，选取其中的最小值，作为样本及S的最优二分方案。

$ GainGini(D,A)=\frac {D1}{D}Gini(D_1)+\frac {D2}{D}Gini(D_2) $

根据训练数据集，从根节点开始，递归的对每个节点进行以下操作来构建二叉决策树:

1. 从节点的训练数据集D计算现有特征对该数据集的基尼指数(Gini)。此时，对每一个特征A，对其可能取得每一个值a，根据“样本A = a的结果是‘是’或‘否’”将D分割成D1，D2两部分，利用式①计算A = a 时的Gini。
2. 在所有可能的特征A以及它们所有可能的切分点a中选择Gini最小的特征及其对应的切分点作为最优特征和最优切分点，然后依据最优特征与最优切分点从现节点生成两个子结点，最后将训练数据集依据特征分配到两个子结点中去。
3. 对两个子结点递归的调用上面两步直至满足停止条件。
4. 生成CART决策树。

PS：算法的停止条件是“节点的样本个数 < 预定阈值”或“样本集合的Gini < 预定阈值（样本基本属于同一类）”或“无更多特征”。




