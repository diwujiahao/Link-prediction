# Trans-E

## 相关论文

Translating Embeddings for Modeling Multi-relational Data （2013 NIPS）

## 方法综述

Trans-E的目的：为了解决多关系数据（multi-relational data）的处理问题。

TransE的直观含义：就是TransE基于实体和关系的分布式向量表示，将每个三元组实例（head，relation，tail）中的关系relation看做从实体head到实体tail的翻译，通过不断调整h、r和t（head、relation和tail的向量），使（h + r） 尽可能与 t 相等，即 h + r = t。
 
TransE与其他方法的区别：方法简单易扩展，且效果接近。
 
模型问题：它只适合处理一对一的关系，不适合一对多/多对一的关系。举个例子，有两个三元组（中国科学院大学，地点，北京）和（颐和园，地点，北京），使用TransE进行表示的话会得到中国科学院大学的表示向量和颐和园的表示向量很接近，甚至完全相同。但是它们的亲密度实际上可能没有这么大。
 
 ---
 
# 论文记录：Translating Embeddings for Modeling Multi-relational Data（2013 NIPS）

## 文章概述

Trans系列的第一篇文章。目标是提出模型来解决多关系数据的编码问题，模型的特点有 :

- 通用、易训练
- 针对大规模数据
- 不需要额外的知识

> TransE, an energy-based model for learning low-dimensional embeddings of entities.

基本思想是对于三元组(h, r, t)，前件的向量表示h与关系的向量表示r之和与后件的向量表示t越接近越好(即h + r ≈ t)。目标是把三元组翻译成低维度稠密embedding向量。

![](../note_image/屏幕快照\ 2019-06-04\ 下午12.11.25.png "基本思想示意图")

模型初衷是为了建模树形的层次结构而设计的，但结果表明在大多数关系中表现都很好。

应用举例：社会关系分析/推荐系统/知识图谱。

## 主要贡献

提出了多关系数据的建模方法Trans-E，并在Wordnet和Freebase数据集中的链接预测任务中验证了模型的有效性。

## 具体方法

优化的目标函数使用带negative sampling的max margin损失函数。（借鉴SVM）。

损失函数的具体定义 :

![](../note_image/屏幕快照\ 2019-06-04\ 下午1.25.49.png)

损失函数见公式(1)。

负例的构造见公式(2)。将正样本三元组中的前件或后件替换为一个随机的实体已获取负样本。

优化方法使用mini-batch随机梯度下降。

对每个实体的向量加入约束：L2范数为1。但关系则没有约束。（重要）

具体代码如下图 :

![](../note_image/屏幕快照\ 2019-06-04\ 下午1.39.30.png)

## 实验

论文中数据集为两个知识图谱Wordnet和Freebase，以链接预测任务作为实验任务。

模型评价指标 : hits@10。(论文引用：hits@10, which we believe are a clearer evaluation of the performance of the methods in link prediction.)








