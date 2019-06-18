# 题目名称：Inductive Representation Learning on Large Graphs（NIPS 2017）

## 论文概述

大图中节点的低维嵌入在预测任务中被证明十分有效。然而，大多数现有的方法都要求图中的所有节点都在嵌入训练期间出现，这些先前的方法天生具有转导性，不能自然地推广到不可见的节点。

本文提出一个模型GraphSAGE，利用节点的特征信息（文本属性），可以为之前没见过的节点有效的生成节点向量。

> While we focus on feature-rich graphs (e.g., citation data with text attributes, biological data with functional/molecular markers), our approach can also make use of structural features that are present in all graphs (e.g., node degrees).

本文使用采样技术，将一个节点部分邻居的特征聚合，来修正当前节点向量。而不是使用为每个节点训练单独的向量。

> However, previous works have focused on embedding nodes from a single fixed graph, and many real-world applications require embeddings to be quickly generated for unseen nodes, or entirely new (sub)graphs.

> 图中的边数量稀疏也和该问题痛点一致

inductive节点嵌入相比于transductive要难。一个inductive的框架不仅要识别节点自身属性，还要识别节点邻居的结构属性。

截止2017年，GCN仅仅被应用在Transductive思想的静态图嵌入。本文将GCNs扩展到归纳无监督学习的任务，并提出一个框架将GCN方法推广到使用可训练的聚合函数。

## 主要贡献

- 提出了GraphSAGE模型，使用节点的属性特征和节点邻居的结构特征进行局部编码。可以看做GCN的扩展。
- 通过采样节点邻域有效地平衡了性能和运行时间，非常适用于属性丰富的大图。

## 具体方法

方法的核心思想是：学习如何聚合一个节点的邻居特征信息

### 节点向量生成

我们训练了一组聚合器函数，这些函数学习如何从节点的本地邻域聚合特征信息如下图。在测试或推理时，我们使用经过训练的系统，通过应用所学的聚合函数为完全不可见的节点生成嵌入。在之前的节点嵌入生成工作之后，我们设计了一个无监督损失函数，它允许在没有特定任务监督的情况下训练GraphSAGE。我们还证明了GraphSAGE可以在完全监督的方式下进行训练。

![节点向量生成示意图](../note_image/屏幕快照\ 2019-06-18\ 下午5.56.28.png)

节点生成伪代码：

![](../note_image/屏幕快照\ 2019-06-18\ 下午6.54.03.png)

其中的AGGREGATE函数选择：

- Mean
- LSTM
- Pooling

### GraphSAGE参数学习



## 相关论文


















