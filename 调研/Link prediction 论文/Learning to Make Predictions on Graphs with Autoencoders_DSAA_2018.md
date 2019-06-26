# Learning to Make Predictions on Graphs with Autoencoders(DSAA 2018)

## 文章概述

文章方法针对的任务：链路预测和半监督的节点分类。

本文提出了一个新的autoencoder架构，可以端到端地联合学习本地图结构和节点特征。

之前的方法是多步的，不利于调优。




## 核心贡献

提出了一个自编码器结构，解决了以下难点：

- 稀疏性：未知连边通常远多于已知
- 复杂性：图结构的复杂，连边有无向，连边有无权重等
- side information：节点/边是有描述性特征的
- 计算效率高

此外，该自编码结构的新颖之处在于能够有效地训练端到端联合、多任务学习(MTL)的链路预测和节点分类任务。

## 具体方法

模型的输入是一个子图，以邻接矩阵的形式。（1：有边；0：没有边；UNK：不确定）



## 实验结果


## 相关论文



代码链接：https://github.com/vuptran/graph-representation-learning