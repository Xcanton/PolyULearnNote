# Routing Protocol

网络可以通过图来表征，并且图的通路是有代价的，那么如何找到最低代价的通路（the least-cost path）就是路由协议需要研究的问题。

## Dijkstra's Algorithm（迪杰斯特拉算法）

<figure><img src="../.gitbook/assets/image (163).png" alt=""><figcaption><p>操作</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (161).png" alt=""><figcaption><p>Dijsktra‘s Algorithm</p></figcaption></figure>

* 初始化将开始节点，和其的邻接节点作为候选
* 循环直到所有的节点都在N中
  * 根据上一轮最小的候选作为当前更新的node，算其邻接节点的cost
  * 更新N
  * 将这当前更新的node加入N（第一轮一定是N）

那么每次更新的时候，一定是第n个节点是最近的

## Routing Algorithm Classification

### Global or decentralized?

肯定是decentralized，因为global需要每个router的信息和通路都知道

### Static or Dynamic？

肯定是dynamic，routes变化很快

## Distance Vector Algorithm

<figure><img src="../.gitbook/assets/image (165).png" alt=""><figcaption><p>Distance Vector Algorithm</p></figcaption></figure>

每个节点都有对目标节点的预估代价，然后broadcast到它的邻居，它的邻居可以根据自己到它的实际cost和它的预估代价计算。

如果有个节点变了，那它只用通知邻居，更新影响到的通路。所以可以是dynamic的。
