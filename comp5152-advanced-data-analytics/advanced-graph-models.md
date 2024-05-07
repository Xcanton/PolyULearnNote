# Advanced Graph Models

## Node Embeddings

Intuition: Map nodes to d-dimensional embeddings such that similar nodes in the graph are embedded close together.&#x20;

Goal: Map nodes so that similarity in the embedding space (e.g., dot product, cosine similarity) approximates similarity in the network.&#x20;

### 2 Key Components

1.  Encoder

    Map a node to a low-dimensional vector
2.  Similarity Function

    Defines how relationships in the input network map to relationships in the embedding space

### 随机游走和Node2Vec的缺点 Limitations of Random Walk and Node2Vec

1.  需要较大的空间存储

    O(|V|) parameters are needed

    1.  没有在节点间共享参数

        No sharing of parameters between nodes
    2.  每个节点持有独特的embedding

        Every node has its own unique embedding
2.  embedding需要训练推理保持一致

    Inherently Transductive 导致的问题是冷启动问题

    1.  不能为训练没见过的节点生成embedding

        Can not generate embeddings for nodes that are not seen during training
3.  没有和节点特征进行交互

    Do not incorporate node features&#x20;

    1.  很多图有值得关注的特征属性

        Many graphs have features that we can and should leverage

### 深度网络处理图embedding的难点

1.  输入的大小不定，且没有固定的拓扑结构

    Arbitrary size and complex topological structure
2.  没有固定的节点顺序或者参考节点

    No fixed node ordering or reference point
3.  通常是动态的，并且包含多模态的数据

    Often dynamic and have multimodal features

### 为什么不能用邻接矩阵作为输入

* O(N) parameters
*   对变化图大小不适用

    Not applicable to graphs of different sizes
*   不允许图节点顺序改变

    Not invariant to node ordering

## GCN 图卷积神经网络 Graph Convolutional Networks

* 学习怎么通过图的邻近节点计算节点的特征

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

* Key Idea
  * Generate node embeddings based on local network neighborhoods
* Intuition&#x20;
  * nodes aggregate information from their neighbors

### 怎么聚合临近节点信息 Neighborhood Aggregation

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

* 本质上是加权求和
* 对当前节点的周围信息加权求和
* 再通过可学习的参数，与上一层的输出加权
* 最后经过非线性激活函数

### 怎么选择损失函数&#x20;

#### Supervised Training

可以直接采用某些有监督任务进行训练

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

#### Unsupervised Training

记得我们的初衷是相似的节点具有相似的embedding（Similar nodes have similar embeddings）

$$
L = \sum_{z_u, z_v} CE(y_{(u,v)},\ Decoder(z_u, z_v))
$$

* 当节点相似时y为1
* ce是交叉熵损失
* Decoder是计算相似度的函数，比如dot product
* 节点相似度也可以通过类似Random walks等方式获取

### 模型训练步骤

1.  定义一个近邻聚合函数

    Define a neighborhood aggregation function
2.  定义一个embedding的损失函数（相似度计算）

    Define a loss function on the embeddings
3. 训练
4.  推理：生成节点embedding

    Generate embeddings for nodes as needed; even for nodes we never trained on

## GraphSAGE

GraphSAGE的基本思想是保留自身节点的表征，通过可变的聚合函数将周边节点的表征映射到自身向量中。

Any differentiable function that maps the set of vectors in N(u) to a single vector

$$
h_v^k=\delta(A_k*[AGG(\{h_u^{k-1}, \forall u \in N(v) \})], B_kh_v^{k-1})
$$

* 简而言之，就是将GCN的向量相加替换成了向量Concatenate
* 聚合方式是生成的

其中聚合方式也有多种，原始论文中用的是Mean，也就是GCN的加权平均方式。

$$
MEAN\_AGG(h_v^k) = \delta (W_k \sum_{u \in N(v)} {\frac {h_u^{k-1}} {|N(v)|}} + B_kh_v^{k-1})
$$

* 还可以采用Pooling策略，element-wise min/min/mean across the coordinates
* 也可以将邻近节点reshuffled，然后通过LSTM训练表征

并且GraphSAGE对向量采用了L2 normalization，但是实验证明不一定有效。

## GAN Graph Attention Network

本质上是为了提升节点融合的效果，也有一个玩意专门做加权求和的，就是Attention。GAN就是将Attention引入图神经网络。

*   Goal：为了将动态的模糊重要性引入邻居节点融合计算中

    Specify arbitrary importance to different neighbors of each node in the graph
* Idea：将 $$h_v^k$$和其他节点做attention
  * Nodes attend over their neighborhoods' message
  *   隐式为不同的邻近节点指定权重

      Implicitly specifying different weights to different nodes in a neighborhood

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

对于每两个节点，我们采用节点映射后的向量拼接，然后再次白化处理：

$$
\alpha (W_k h_u^{k-1}, W_k h_v^{k-1})=Linear(Concat (W_k h_u^{k-1}, W_k h_v^{k-1}))
$$

让我们先计算attention的相似度系数（attention coefficient）$$e_{vu}$$ ：

$$
e_{vu} = \alpha (W_k h_u^{k-1}, W_k h_v^{k-1})
$$

还需要对这个相似度系数标准化，通常用的是softmax函数：

$$
a_{vu} = \frac {\exp(e_{vu})} {\sum_{k \in N(v)} {\exp(e_{vk})}}
$$

最后对节点v计算邻近节点的Attention权重：

$$
h_v^k = \delta(\sum_{u \in N(v)}a_{vu}W_kh_u^{k-1})
$$

当然，这个attention也可以采用multihead-attention，多头输出可以采用拼接或者mean。

### GAN的好处

1.  主要好处：允许隐式建模不同邻居节点的重要性

    Key benefit: Allows for implicitly specifying different importance values to different neighbors
2.  计算效率高

    Computationally efficient

    1.  可以并行计算所有图和网络

        Computation of attentional coefficients can be parallelized across all edges of the graph
    2.  聚合可能可以并行计算所有的节点

        Aggregation may be parallelized across all nodes
3.  迁移方便（简单本地化）

    Trivially localized

    1.  只考虑了局部的邻近网络结构

        Only attends over local network neighborhoods
4.  感知能力强

    Inductive capability

    1.  在节点层面共享了参数

        It is a shared edge-wise mechanism
    2.  不需要依靠全局的图信息

        It does not depend on the global graph structure
