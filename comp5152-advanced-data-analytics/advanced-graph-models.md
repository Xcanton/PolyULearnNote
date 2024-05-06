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

## 图卷积神经网络 Graph Convolutional Networks

* 学习怎么通过图的邻近节点计算节点的特征

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

* Key Idea
  * Generate node embeddings based on local network neighborhoods
* Intuition&#x20;
  * nodes aggregate information from their neighbors

### 怎么聚合临近节点信息 Neighborhood Aggregation

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

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
