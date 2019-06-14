# TransNet - Translation-Based Network Representation Learning for Social Relation Extraction（IJCAI 2017）

### 文章概述

传统网络表示学习方法（NRL）将网络中的链接看做0/1或一个连续值，忽略了连边的丰富特征。其中遇到稀疏的问题，严重影响机器学习性能。

> Conventional network representation learning (NRL) models learn low-dimensional vertex representations by simply regarding each edge as a binary or continuous value. 
> 
> However, there exists rich semantic information on edges and the interactions between vertices usually preserve distinct meanings, which are largely neglected by most existing NRL models. 

典型的KRL模型，如TransE，只有在两个实体之间的关系用一个标签进行特殊标注时，才能够很好地按形式进行转换。

在社交网络中，边缘往往没有标注明确的关系，在大规模的网络中，通过胡曼的努力来标注边缘也是一项费时的工作。为了解决这一问题，我们提出了通过NLP技术自动获取交互文本信息之间的关系。

### 主要贡献

- 提出了一个基于翻译的模型TransNet。
- 本文提出了Social Relation Extraction（SRE）任务并设计评估方法。
- 为SRE任务构造三个数据集。

### Social Relation Extraction问题

本文提出了Social Relation Extraction（SRE）任务并设计评估方法。问题旨在建模和预测社会关系网络中的关系。

该问题与知识图谱中关系抽取（relation extraction）最大的区别是：

- 知识图谱中关系有明确预定义，本问题中关系模糊，隐藏在interactive text information中。
- 社交网络中的关系动态且复杂，无法用简单的label标记。

> 问题定义：Formally, we define the problem of SRE as follows. Suppose there is a social network G = (V,E), where V is the set of vertices, and E ⊆ (V × V ) are edges between vertices. Besides, the edges in E are partially labeled, denoted as EL. Without loss of generality, we define the relations between vertices as a set of labels, instead of a single label. Specifically, for each labelled edge e ∈ EL, the label set of edge e is denoted as l = {t1,t2,...}, where each label t ∈ l comes from a fixed label vocabulary T .

### 核心方法

模型框架：

![](../note_image/屏幕快照\ 2019-06-14\ 下午1.05.42.png)

包含两个核心组件：翻译部分和链接表示部分。

### 相关工作

network representation learning（NLR）被分为三类：

- to learn representations from local network structure. 
- capture the global structure and community patterns.
- incorporate heterogeneous information into NRL

##### 翻译机制

对每个节点使用两个向量表示，分别对应头结点和尾巴节点。

每条边对应多个关系的集合。

利用编码后的边向量与节点向量进行翻译模型训练。

##### 自编码机制

01向量编码为稠密向量再解码为01向量。

由于0多1少，分类器倾向于0，损失函数中加入更新权重。

### 源代码&数据集

> https: //github.com/thunlp/TransNet.





















