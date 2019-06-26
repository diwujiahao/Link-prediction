# 论文题目：Structural Deep Network Embedding（SIGKDD 2016）


## 论文概述

图嵌入的挑战：

- 高度非线性
- 保留结构信息[局部网络/全局网络]
- 稀疏

本文提出了一个结构化的深度神经网络嵌入模型SDNE，通过半监督的方式来学习节点表示。模型设计了多层架构和非线性激励，同时提出了利用一阶近似和二阶近似共同学习网络结构的方法：

- 一阶：有监督——学习本地网络结构——一阶近似用于获取局部的pairwise相似度信息
- 二阶：无监督——捕捉全局网络结构——二阶近似用于获取全局网络结构特征并弥补一阶pairwise稀疏问题

模型同时学习了本地和全局网络结构，并在稀疏图上鲁棒。


## 主要贡献

- 提出了一种结构化的深度网络嵌入方法，即SDNE，多层非线性结构可以捕捉高阶非线性特征，并对稀疏图鲁棒。（作者自称最早使用深度学习做网络表示学习）
- 提出了一种新的半监督结构的深度模型，同时优化了一阶和二阶近似，同时学习了局部特征和全局特征。
- 在5个实际数据集和4个应用场景上对该方法进行了广泛的评估。

## 具体方法

### 问题定义

> DEFINITION 2. (First-Order Proximity) The first-order prox- imity describes the pairwise proximity between vertexes.

> DEFINITION 3. (Second-Order Proximity) The second-order proximity between a pair of vertexes describes the proximity of the pair’s neighborhood structure. 

Second-Order Proximity 的前提假设：如果两个节点邻居交集多，则他们倾向于相似。

### 模型

模型架构：

![模型架构](../note_image/屏幕快照\ 2019-06-19\ 下午4.16.45.png)

Second-Order Proximity 损失函数：

![](../note_image/屏幕快照\ 2019-06-19\ 下午4.18.08.png)

first-Order Proximity 损失函数：

![](../note_image/屏幕快照\ 2019-06-19\ 下午4.18.17.png)

损失函数：

![](../note_image/屏幕快照\ 2019-06-19\ 下午4.17.57.png)

训练复杂度：O(ncdI)，线性与n

- n is the number of vertexes
- d is the maximum dimension of the hidden layer
- c is the average degree of the network  
- I is the number of iterations.





代码链接：https://github.com/suanrong/SDNE/blob/master/picture/TimeCompare.png










