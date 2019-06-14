# 博客：社交网络中的Link Prediction

相关链接：https://blog.csdn.net/a358463121/article/details/79350292

### 社交网络的几个性质：

- power law degree distribution：链接分布不均匀，少部分人占据了大多数链接。长尾效应明显。

- the small world phenomeno：六度空间--任何两个人之间所间隔的人不会超过六个。

- the community structure (clustering effect)：社交网络里面会有很多个小群体，他们都相互认识彼此。

### 方法分类：

- Path-based Methods

1. 节点间最短路径：一个最直接的预测方法就是计算两个结点间的距离，然后根据距离的大小来预测，两个结点越近那么就越容易在未来建立联系。但是在上百万的结点下直接用dijkstra算法是非常低效的。相反，我们可以利用small world phenomenon来提高我们的效率。
2. 节点间路径的数量（Katz (Exponentially Damped Path Counts)）：用x，y之间存在的路径的数量来衡量它们的距离。然而路径有长有短，那些很长的路径其实是没什么说服力的，于是引入指数衰减机制随着路径长度进行衰减。（Hitting Time：为了加快计算速度，可以使用蒙特卡洛的技术来估计x，y的路径的数量。）
3. 带重启的随机游走（Rooted PageRank）：

- Neighbor-based Methods

1. 公共邻居数量（Common Neighbors）：当两个用户有着很多个相同的邻居，我们就认为这两个用户很有可能建立联系。
2. 邻居集合相似性（Jaccard’s Coefficient）：将每个节点的邻居数量考虑进去。
3. 考虑邻居重要性（Adamic-Adar (Frequency-Weighted Common Neighbors)）：是对Common Neighbors的改进，当我们计算两个相同邻居的数量的时候，其实每个邻居的“重要程度”都是不一样的，我们认为这个邻居的邻居数量越少，就越凸显它作为“中间人”的重要性。
4. 共同好友互为好友的数量（Friendes-mearsure）：比公共邻居多考虑一层。
5. 朋友多的人更愿意交朋友（Preferential Attachment）：基于这思想,用他们两个用户的好友数量的乘积作为评分。
6. 考虑用户行为（Link Prediction with Personalized Social Influence）。
7. 考虑subgraph（Link Prediction with Personalized Social Influence）：基本思想是，用广度优先搜索就可以得到每个结点不同深度的子图，然后利用这些结构信息来embedding，将不同深度得到的embedding concat在一起得到这个结点的embedding。最后用这些embedding的余弦相似度来做link prediction。
















