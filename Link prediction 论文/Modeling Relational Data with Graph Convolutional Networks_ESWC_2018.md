# 论文名称：Modeling Relational Data with Graph Convolutional Networks_ESWC_2018

## 论文概述

提出了一种图神经网络的框架来建模关系数据，解决链路预测和实体分类问题。

## 主要贡献

- 将GCN框架应用于建模关系数据（Link prediction / Entity classification）
- 介绍了参数共享和增强稀疏约束的技术，并应用于多关系图。
- 将因子分解模块（DistMult）作为解码可以提升模型性能。


## 具体方法

节点向量可以初始化为one-hot向量，也可以建模预定义的特征向量。

网络架构：
![网络架构](../note_image/屏幕快照\ 2019-06-17\ 下午3.03.45.png)

更新公式：
![更新公式](../note_image/屏幕快照\ 2019-06-17\ 下午3.04.32.png)

Link prediction模型：
![Link prediction模型](../note_image/屏幕快照\ 2019-06-17\ 下午3.03.58.png)

## 相关论文

- 论文中提到类似的方法框架可以用预定义的特征来初始化向量：Kipf, T. N., and Welling, M. 2017. Semi-supervised classi- fication with graph convolutional networks. In ICLR.

- 信息传递网络：Gilmer, J.; Schoenholz, S. S.; Riley, P. F.; Vinyals, O.; and Dahl, G. E. 2017. Neural message passing for quantum chemistry. arXiv preprint arXiv:1704.01212.


















