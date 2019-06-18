# Trans-R

## 相关论文

Learning Entity and Relation Embeddings for Knowledge Graph Completion（AAAI 2015）

## 方法综述

Trans-E和Trans-H假设实体和关系在一个语义空间，相似的实体在空间中的相似位置。实际中不同关系可能关注实体的不同方面，Trans-R模型对不同关系建立各自的关系空间，计算时先将实体映射到关系空间再进行计算。在关系空间通过训练使得hr + r ≈ tr。目标函数和训练方法和TransE模型一模一样。

示意图如下所示：
![](../note_image/屏幕快照\ 2019-06-04\ 下午5.19.17.png)

---

# 论文名称：Learning Entity and Relation Embeddings for Knowledge Graph Completion（AAAI 2015）

## 文章概述

Trans-E和Trans-H都将实体和关系嵌入在同一个语义空间中。但在实际中，一个实体可能具有多种关系，每种关系关注实体的不同方面，所以将其全部嵌入在同一个语义空间中是一种不精准的做法。

本文提出的Trans-R模型将实体和关系建模在不同的语义空间。在训练或预测时，先将实体从实体空间映射到相关的关系空间，再进行Translation。

现有的挑战：

- 知识图谱中节点所对应的实体拥有不同的类型和属性
- 知识图谱中的边可以链接不同类型的实体

这导致传统的链接预测方法无法解决knowledge graph completion问题。

论文引用：To address this issue, we propose a new method, which models entities and relations in distinct spaces, i.e., entity space and multiple relation spaces (i.e., relation-specific entity spaces), and performs translation in the corresponding relation space, hence named as TransR.

又由于同一个关系可能细分为很多情况，例如：北京-位于-中国/北大-位于-中国。所以文章对Trans-R进行扩展，对同一个关系中的不同实体对进行聚类，每一类单独训练一个关系向量。(使模型更加精细化)

## 主要贡献

- 提出了Trans-R模型
- 在Trans-R模型的基础上扩展为CTransR(cluster-based TransR)
- 在公开数据集上验证了模型的有效性

## 具体方法

### Trans-R

由于实体向量需要经过转换后再与关系向量相加，所以其维度不要求一致。

对于每个关系r，文章设置一个映射矩阵Mr，将实体向量h和t转换为hr和tr。

![](../note_image/屏幕快照\ 2019-06-04\ 下午5.52.42.png)

同时加入约束条件:h,r,t,hr,tr的二范数均小于等于1。

### CTrans-R

以上模型中的一个关系对应一个向量，这是不够精细的。为了更好地建模这些关系，作者结合了piecewise linear regression (Ritzema and others 1994)的思想来扩展Trans-R。

对于一个特定的关系r，将其对应的实体对(h,t)利用(h-r)为特征聚类为多组，每组实体对对应一个关系向量，每个关系对应一个转换矩阵。（实体和关系的embedding利用Trans-E的结果进行初始化）

![](../note_image/屏幕快照\ 2019-06-04\ 下午6.07.33.png)

同样，CTrans-R也对h,r,t,mapping matrix加入了约束条件。

损失函数如下所示:

![](../note_image/屏幕快照\ 2019-06-04\ 下午6.11.11.png)

## 实验

实验数据集 :

- WordNet
- Freebase

文章在三个任务中验证了模型的有效性 :

- link prediction
- triple classification
- relational fact extraction

构造负例的方法参考论文:Wang, Z.; Zhang, J.; Feng, J.; and Chen, Z. 2014. Knowl- edge graph embedding by translating on hyperplanes. In Proceedings of AAAI, 1112–1119.

优化方法: 随机梯度下降

链接预测评价指标: mean rank / Hits@10

## 文章总结

待改进的点:

- 现有方法都没能融入一些relation pattern（例如有些关系具有传递性）
- CTrans-R可以继续探索更复杂的模型









