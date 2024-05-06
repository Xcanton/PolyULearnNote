# Graph Data

图是一种通用语言，用来表征和分析实体及实体关系。

Graphs are a general language for describing and analyzing entities with relations/interactions.&#x20;

跟图有关的任务：

* Node Classification
  * Predict a property of a node
* Link Prediction
  * Predict whether there are missing links between two nodes
* Graph classification
  * Categorize different graphs
* Clustering&#x20;
  * Detect if nodes form a community
* Graph Generation
* Graph Evaluation

## 如何定义一张图 How do you define a graph?

1. 节点是什么
2. 边是什么
3.  选择一个合适的网络表征形式

    Choosing of the proper network representation of a given domain/problem determines our ability to use networks successfully

## 二部图Bipartite Graph

二部图是一个节点可以被划分为两个不相交子集，并且连接只发生在两个不相交的子集间。并且两个子集是相互独立的

A bipartite graph is a graph whose nodes can be divided into two disjoint sets U and V such that every link connects a node in U to one in V; that is U and V are independent sets.&#x20;

## 如何表示一个图 Representing Graphs

### Adjacency Matrix

### Edge List

### Adjacency List

### Node and Edge Attributes

* Weight
* Ranking
* Type
* Sign

## 节点层面的特征 Node-level Features

目的：刻画节点的结构和在图中的位置

### 度 Node Degree

*   表示的是有多少边

    The degree kv of a node v is the number of edges (neighboring nodes) the node has
*   度将所有临近节点平等对待

    Treats all neighboring nodes equally
*   计算度的时候，不关心节点的重要性

    Node degree counts the neighboring nodes without capturing their importance

### 中心性 Node Centrality

#### 介数中心性 Betweenness Centrality

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

$$
c_v=\sum_{s \not = v \not = t} \frac {shortest\ paths\ between\ s\ and\ t\ that\ contains\ v}{shortest\ paths\ between\ s\ and\ t}
$$

*   计算的是当前节点是多少个最路中的节点

    A node is important if it lies on many shortest paths between other nodes
*   更高的介数中心性，意味着更稳固的人际关系

    Higher betweenness, Stronger interpersonal ties

#### 紧密中心性 Closeness Centrality

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

$$
c_v = \sum_{u \not = v} \frac 1 {shortest\ path\ length\ between\ u\ and\ v}
$$

*   衡量的是它是否是到其他节点最小的路径

    A node is important if it has small shortest path length to all other nodes

### 聚类系数 Clustering Coefficient

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

$$
e_v=\frac {edges\ among\ neighboring\ nodes} {\mathcal{C}_2^{neighbor\ cnt}} \in [0,1]
$$

*   衡量的是临近节点的连接程度

    Measures how connected v's neighboring nodes are

## Edge-Level ML Tasks

* Users interacts with items
  * Nodes: users and items
  * Edges: user-item interactions
*   目标： 给用户推荐可能喜欢的商品

    Recommend items users might like. Recommend related items to users.&#x20;

## Link-level prediction task

*   任务是预测在图中是否有新的边（潜在的关系）

    The task is to predict new links based on existing links

可以用两种方式训练这个网络：

1.  随机丢弃节点，并还原连接信息

    Links missing at random

    Remove a random set of links and then aim to predict them
2.  根据时序训练

    Links over time

## 关系层面的特征 Link-Level Features

### Distance-based feature

<figure><img src="../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

* 两个节点的最短路径的长度。
* 但是这个特征没办法反映节点的度。

### Local neighborhood overlap

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

* 衡量的是两个节点共享的临近节点的情况。

### Global neighborhood overlap

通过邻接矩阵相乘，可以相乘n次就能得到距离为n的通路有多少个

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

#### Katz Index

加权求和两个节点间所有的通路的数量。

## 图表征学习 Graph Representation Learning

* 目标
  *   通过机器学习等方式高效地得到图表征

      Efficient task-independent feature learning from machine learning with graphs

      * 因为每次构建图特征很麻烦
*   这是一个无监督学习的方式

    This is an unsupervised way of learning node embeddings

    * no node labels
    * no node features
    * directly estimate a set of coordinates of a node so that some aspect of the network structure is preserved
*   这个embeddings是与task无关的

    These embeddings are task-independent

Embedding的好处：

*   将节点映射进同一个向量空间中

    map nodes into an embedding space
*   用向量表征他们在图中的相似度关系

    Similarity of embeddings between nodes indicates their similarity in the network
*   表征网络的信息

    Encode network information
*   能够为下游任务提供潜在信息

    Potentially used for many downstream predictions

### 随机游走 Random Walk

原理是：每个节点都有自己的随机初始化向量，随机选择一个点，然后从当前点的随机临近节点中选取一个，优化两个向量相乘的概率为1。

* 也有用cosine相似度替换dot product的
* 并且采取一定的游走策略
* 通过Softmax限制
* 全局优化的目标是概率的连乘，也就是取对数后的累加
  * 本质上也算是信息上

<figure><img src="../.gitbook/assets/image (332).png" alt=""><figcaption></figcaption></figure>

#### Random Walk的好处 Why Random Walks？

* 较强的表现能力 Expressivity
  *   可以灵活的表征节点的局部信息和高阶近邻信息

      Flexible stochastic definition of node similarity that incorporates both local and higher-order neighborhood information
* 高效的 Efficiency
  *   不需要考虑所有的节点对，只需要考虑相邻的节点

      Do not need to consider all node pairs when training, only need to consider pairs that co-occur on random walks

### Node2Vec

*   Random Walk有个问题就是对局部的结构刻画不好，并不能很好保留局部网络的特征

    The DeepWalk method performs random walks randomly which means that embeddings do not preserve the local neighborhood of the node
* Node2Vec增加了参数P和参数Q
  * Q控制从未访问过的节点中选取一个访问的概率，为1/q
    * 能够控制较大的邻近节点的发现数量
    * 控制社区的推理和构造复杂度
  * P控制返回上一个节点的概率，为1/p
  * 还保留了行走的概率1

<figure><img src="../.gitbook/assets/image (334).png" alt=""><figcaption></figcaption></figure>

*   出发点 Idea

    可以通过灵活的、偏见的随机游走来交替局部结构和全局结构的构建

    * 本质上是BFS和DFS的交替
    * BFS相当于P的值很小，不怎么返回上一个节点
    * DFS相当于Q的值很小，不怎么找当前未访问过的节点新访问

<figure><img src="../.gitbook/assets/image (333).png" alt=""><figcaption></figcaption></figure>

