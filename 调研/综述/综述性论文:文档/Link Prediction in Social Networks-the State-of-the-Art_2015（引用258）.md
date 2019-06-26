# 论文标题：Link Prediction in Social Networks:the State-of-the-Art（SCIENCE CHINA 2015）

## 论文概述

本文的目的是综合回顾、分类、讨论社交网络中的链路预测问题。

> A social network is a social structure made up of a set of social actors and a set of the ties between these actors. A social network can be visualized as a graph, where nodes represent actors/participants (individuals, organizations, et al.) and edges (i.e. links) correspond to ties/interactions/relationships between actors.

社交网络的两大挑战：

- 不完整性
- 动态变化（节点和链接都会变）

Link prediction应用：

- 推荐系统（搜索、电商、社交）
- 完善现有的社交网络
- 生物信息学（基因、健康）
- 安全

- Link prediction相关会议：WSDM, SDM, KDD, JCDL, ICDM, CIKM, ICDM, WWW, ISWC, IJCAI, ICML, SIGCOMM, NIPS, ASONAM。
- Link prediction相关期刊：Nature, Physical Review, Physica A, TKDD, TWEB, DKE, JSS, JMLR, Social Networks, Computer Networks

## 主要贡献

- 总结Link prediction定义
- 总结一般Link prediction模型框架
- 总结Link prediction相关技术
- Link prediction中困难问题的解决方法
- Link prediction在社交网络中的应用
- 总结Link prediction未来的挑战


## 总结Link prediction定义

对于社交网络G(V,E)，V表示节点集合，E表示链接集合。Link prediction希望预测新链接或删除链接，针对未来一段时间的变化，或针对现有的缺失和错误链接。

## 总结一般Link prediction模型框架

![一般模型框架](../../note_image/屏幕快照\ 2019-06-12\ 下午8.53.52.png)

### 基于相似度的方法

计算两个未连接节点的相似度（相似度的定义十分重要，且可以十分复杂），高相似度的节点对被认为有链接。一般寻找top k个节点作为预测结果。

- 基于节点特征
- 基于拓扑特征
	- 邻居
	- 路径
	- 随机游走 
- 基于社交网络特征

### 基于学习的方法

将连接预测问题转换为二分类问题。通过定义特征（相似度特征，节点本身特征，外部知识等），利用现有连边进行监督学习训练二分类模型，并对未连接节点对进行预测。

- 基于分类模型
- 基于概率图模型
- 基于矩阵分解

## 总结Link prediction相关技术

![分类](../../note_image/屏幕快照\ 2019-06-12\ 下午9.06.01.png)

## Link prediction中困难问题的解决方法

- 考虑时间的链路预测
- 异质网络的链路预测
- 链接活跃/非活跃的链路预测
- Bipartite Networks中的链路预测
- 链接可消失的链路预测
## Link prediction在社交网络中的应用

略

## 总结Link prediction未来的挑战

- 消失链接预测
- 节点可变的链接预测
- Overcoming imbalance（已有链接比缺失链接多很多）
- 社会理论的融入（不仅仅是基于节点信息和拓扑结构）
- 异质网络中的链接预测问题
- 评估方法和数据集



































