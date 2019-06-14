# 1、_Link prediction 概述_

## 1.1、任务定义

### 问题定义

网络中的链路预测(Link Prediction)是指，如何通过已知的网络节点以及网络结构等信息预测网络中尚未产生连边的两个节点之间产生链接的可能性。这种预测既包含了对未知链接（exist yet unknown links）的预测也包含了对未来链接（future links）的预测。

### 相关细分问题

- Link prediction：对于一个可变网络，预测节点之间的关系。
- Link completion：对于一个网络，根据网络结构推理出那些丢失的边。
- Link reliability：估计一个给定链接的可靠性。

## 1.2、方法归类

- 基于分数的方法（估计链接的分数并选择top-k，对图谱中已有的边信息利用不充分，可以设计算法学习分数的计算方法）
	- 基于公共节点
		- 公共邻居数量
		- 公共邻居集合的杰卡德相似度
		- Adamic-Adar（效果好，考虑了节点的重要性不同。假设邻居多的节点重要，score=公共邻居节点的重要性。）
	- 基于路径
		- 最短路径
		- Katz score
		- rooted PageRank
		- 随机游走到达步数的期望（Expected number of randomo walk steps）
		- SimRank（递归定义）
	- 基于节点特征
		- 节点度数（Preferential attachment）
		- 聚类系数（Clustering coefficient）
- 基于有监督学习（图谱->特征->预测，可以较好地利用已有的边信息）
	- 特征
		- 拓扑特征（假设两个节点相似性越大，存在链接的可能性越大。相似性的定义可以自由设计。）
		- 节点内容特征（不易获取 / 干扰特征多，特征筛选难）
		- 聚合特征
	- 模型
		- 决策树、朴素贝叶斯、神经网络、SVM、KNN、集成方法（bagging、boossting和随机森林等）  
- 基于无监督学习（不需要训练数据。）
	- 对已有网络拓扑结构进行建模	
		- Trans系列（TransE[2]、TransH、TransR[1]、TransD）[4]
	- 对节点或关系的描述信息进行建模
		- [5]
	- 捕捉全局结构和社区模式
- 基于线性代数（基于邻接矩阵等信息，对信息的利用不充分。）
	- SVD分解（低维近似）
	- Kuegis等人利用图的邻接矩阵，并定义一个带参函数F使得两个时刻的邻接矩阵的差异性最小。将链路预测问题转换成线性代数优化问题，之后再通过矩阵变换和降维的方法将问题转换为一维的最小二乘曲线拟合问题。
- 基于概率的方法（可能存在计算复杂的情况）
	- 最大似然估计（处理具有明显层次组织的网络具有较好的精确度，计算复杂度非常高）
	- 贝叶斯网络模型
	- 马尔科夫网络关系模型
	- 网络熵

链路预测问题的主要研究热点逐渐从依赖于节点属性的方法转移到只利用网络结构信息的方法上。显然，后者在理论上也更优美简洁。但是，后者要求图中的连接尽量完整，且丢失了节点和边的特征信息。

## 1.3、本项目的挑战

- 结合数据特点选择模型，如何对于已有信息充分利用
- 将问题建模为二分类问题的挑战
	- 需要评估的候选链接数量很大
	- 样本不均衡
- 落地时图谱规模非常大，要求模型不能太复杂
- 未完待续...

---

# 2、_论文列表_

## 综述性论文
- Link Prediction in Social Networks-the State-of-the-Art_2015（引用258）
- The Link Prediction Problem for Social Networks_2007（引用4000+）

## 方法论文
1. TransR：Learning Entity and Relation Embeddings for Knowledge Graph Completion（AAAI 2015）
	- TransE将实体关系建模在同一语义空间，但一个实体在不同关系中表现的特性可能不同。
2. TransE：Translating Embeddings for Modeling Multi-relational Data （NIPS 2013）
	- Trans系列方法的最原始版本，思想简单粗暴但有效。
3. Fast link prediction for large networks using spectral embedding（Journal of Complex Networks 2017 ）
	- 待补充（不是十分理解） 
4. TransNet- Translation-Based Network Representation Learning for Social Relation Extraction（IJCAI_2017）
	- 针对两个节点的关系不止一种/链接信息丰富的情况进行建模，将Trans思想和自编码器思想结合。
5. A Neural Bag-of-Words Modelling Framework for Link Prediction in Knowledge Bases with Sparse Connectivity_WWW_2019
	- 编码节点及其描述信息，并解码出关系。通过编码节点信息，减少对网络结构的依赖，进而减少稀疏图的影响。

---

# 3、_博客列表_

- [社交网络中的Link Prediction](https://blog.csdn.net/a358463121/article/details/79350292)
- [vedio:Network Analysis. Lecture 18. Link prediction.](https://www.youtube.com/watch?v=2M77Hgy17cg)
- [Trans系列知识表示学习方法梳理](https://zhuanlan.zhihu.com/p/32993044)

		
## 评价方法：

- P、R、F1
- TPR、FPR
- ROC曲线

## 公开数据集：

- BIOBASE database（生物学领域知识库）
- DBLP dataset（论文领域数据集）
- WN18
- FB15K

## 难点与挑战：

- 如何对于已有信息充分利用
- 将问题建模为二分类问题的挑战
	- 需要评估的候选链接数量很大
	- 样本不均衡
- 落地时图谱规模非常大，要求模型不能太复杂
- 未完待续...
