# 1、_Link prediction 概述_

## 1.1、任务定义

### 问题定义

网络中的链路预测(Link Prediction)是指，如何通过已知的网络节点以及网络结构等信息预测网络中尚未产生连边的两个节点之间产生链接的可能性。这种预测既包含了对未知链接（exist yet unknown links）的预测也包含了对未来链接（future links）的预测。

### 相关细分问题

- Link prediction：对于一个可变网络，预测节点之间的关系。
- Link completion：对于一个网络，根据网络结构推理出那些丢失的边。
- Link reliability：估计一个给定链接的可靠性。

### 评价方法

- P、R、F1
- TPR、FPR
- ROC曲线

### 公开数据集

- BIOBASE database（生物学领域知识库）
- DBLP dataset（论文领域数据集）
- WN18
- FB15K

## 1.2、方法归类

![链接预测.svg](https://intranetproxy.alipay.com/skylark/lark/0/2019/svg/218669/1561035928327-f4e83573-c1f2-4146-a08b-0ed8dddaaccd.svg) 

链路预测问题的主要研究热点逐渐从依赖于节点属性的方法转移到只利用网络结构信息的方法上。显然，后者在理论上也更优美简洁。但是，后者要求图中的连接尽量完整，且丢失了节点和边的特征信息。

## 1.3、本项目的挑战

- 结合数据特点选择模型，如何对于已有信息充分利用。
- 将问题建模为二分类问题的挑战。
	- 需要评估的候选链接数量很大
	- 样本不均衡
- 落地时图谱规模非常大，要求模型不能太复杂。
- 图稀疏问题，仅从拓扑结构获取信息明显不足。
- 未完待续...

---

# 2、_论文列表_

> 论文相关笔记见GitHub：https://github.com/diwujiahao/Link-prediction.git

## 2.1 综述性论文

- Link Prediction in Social Networks-the State-of-the-Art_2015（引用258）
- The Link Prediction Problem for Social Networks_2007（引用4000+）

## 2.2 方法论文

1. TransE：Translating Embeddings for Modeling Multi-relational Data （NIPS 2013）
	- Trans系列方法的最原始版本，思想简单粗暴但有效。
2. TransR：Learning Entity and Relation Embeddings for Knowledge Graph Completion（AAAI 2015）
	- TransE将实体关系建模在同一语义空间，但一个实体在不同关系中表现的特性可能不同。
3. Fast link prediction for large networks using spectral embedding（Journal of Complex Networks 2017 ）
	- 待补充（不是十分理解） 
4. TransNet- Translation-Based Network Representation Learning for Social Relation Extraction（IJCAI 2017）
	- 针对两个节点的关系不止一种/链接信息丰富的情况进行建模
	- 将Trans思想和自编码器思想结合。
5. A Neural Bag-of-Words Modelling Framework for Link Prediction in Knowledge Bases with Sparse Connectivity（WWW 2019）
	- 编码节点及其描述信息，并解码出关系。通过编码节点信息，减少对网络结构的依赖，进而减少稀疏图的影响。
6. 基于链路预测的微博用户关系分析（傅颖斌 2014）
	- 以微博为数据源，通过特征提取和机器学习分类的思想完成链路预测。（可作为baseline之一）
	- 数据与我们比较接近，方法思路是基于相似度的，简单，可作为baseline之一。
7. Modeling Relational Data with Graph Convolutional Networks（ESWC 2018）
	- 文中提出了一种基于信息传递的关系图卷积网络（R-GCN），用来提取节点的拓扑特征，可以用预定义属性特征初始化向量。
	- 比较新的方法，可以作为研究方向之一。
8. Inferring Social Ties across Heterogeneous Networks（WSDM 2012）
	- 文章基于半监督学习和概率模型设计了机器学习模型，利用多个异质网络中的信息推断用户的细分关系（朋友，家人等）。
	- 论文比较早，使用的是概率模型，虽然使用了随机梯度下降优化，但预计计算量较大。
	- 文章中提到了一些网络社会学特征，可以尝试利用。
9. Inductive Representation Learning on Large Graphs（NIPS 2017）
	- 扩展性好：提出一个模型GraphSAGE，利用了节点的特征信息（文本属性），可以为之前没见过的节点有效的生成节点向量。
	- 局部计算量小：使用采样技术，将一个节点部分邻居的特征聚合，来修正当前节点向量。而不是使用为每个节点训练单独的向量。
	- 可以作为研究方向之一。
10. Structural Deep Network Embedding（SIGKDD 2016）
	- 利用自编码器对节点的全局拓扑信息进行无监督编码，深度网络对高维特征拟合好，适应稀疏图。
	- 利用连边信息进行局部拓扑的有监督学习
	- 思路类似 [4], 论文4使用自编码器对连边关系进行编码，本文对节点进行编码。




---

# 3、_博客列表_

- [社交网络中的Link Prediction](https://blog.csdn.net/a358463121/article/details/79350292)
- [vedio:Network Analysis. Lecture 18. Link prediction.](https://www.youtube.com/watch?v=2M77Hgy17cg)
- [Trans系列知识表示学习方法梳理](https://zhuanlan.zhihu.com/p/32993044)

		

