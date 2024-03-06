---
description: >-
  Bag-of-Words Representation、Vector Representation & Vector Space Model、Term
  Weighting Schemes
---

# Text Representation

## 词袋表征算法Bag-of-Words Representation

一个文档或者一个句子可以简单近似成一组特征词向量（A document or a sentence can be simply represented as a set (or to say a bag) of words appearing in it.）。在词袋算法中，单词大致被划分成两类：特征词（Representative Words，具有实际意义的词）和非特征词（Non-Representative Words，of that之类没有意义的词）。

<figure><img src="../../.gitbook/assets/image (263).png" alt=""><figcaption></figcaption></figure>

无意义词中，有一类词比较特殊——停用词（Stop Words）。改种词汇出现频率高而且没有意义（Such non-representative words are frequently referred to as stop words），通常被过滤掉（normally filtered out）。

## 向量空间模型（Vector Space Model）

向量空间模型就是从特征词作为评判标准，有出现该词的文档对应向量值是1，没出现的是0。本质上是binary的矩阵。

<figure><img src="../../.gitbook/assets/image (264).png" alt=""><figcaption></figcaption></figure>

一个文档可以用一组是否出现的01特征向量表示（A document is represented as a vector of index terms）

* 每个维度表示一个词表中的词（Each dimension corresponds to an index term in the vocabulary）
* 所以如果有词表中有n个词，那么每个文档用一个n维向量表示
* 这个向量值在文档包含该词的时候是非零的（可能是binary，count或者真实值映射的区间）

## 词权重方法（Term Weighting Schemes，TF-IDF）

本质上是对词（term）t和文档d的相关性，采用一个权重w进行描述。根据不同的权重规则，（t，d）对的权重也不一样。

#### 二维权重方式（Binary Weight Scheme）

<figure><img src="../../.gitbook/assets/image (266).png" alt=""><figcaption></figcaption></figure>

### TF：Term Frequency

<mark style="color:red;">假设</mark>：在文档中出现的高频词（特征词中）可能比低频词具有更强地指示性作用，所以这部分词应该被赋予更高的权重。（Terms that occur frequently within a document may reflect its meaning more strongly than terms that occur less frequently and thus should have high weights.）

<figure><img src="../../.gitbook/assets/image (267).png" alt=""><figcaption></figcaption></figure>

所以用出现数量代替频率，并用特征词的出现次数向量作为文档的tf向量。

### IDF：Inverse Document Frequency

<mark style="color:red;">假设</mark>：只在少数文档中出现的词有利于将他们的文档和其他文档区分开，而在多数文档中都出现的词不具备这种功能。（Terms that are limited to a few documents are useful for discriminating those documents from the rest of the collection; while terms that occur frequently across the entire collection are less useful.）

$$
\mathcal{idf}_t = \log_{10} \frac {N}{{df}_t}
$$

* N是文档数量，即总共的文档库中有多少个文档
* df是document frequency值。

简而言之，<mark style="color:red;">IDF的功能</mark>是制定了文档中词的分布，能够衡量词t在文档集中的重要性（IDF formulates the distribution of terms across the collection as a whole and it is a measure of the general importance of a term t in the document collection.）。

### TF-IDF Weight Scheme

$$
w_{t,d} = {tf}_{t,d} \times {idf}_t
$$

## <mark style="color:red;">例题</mark>：计算TF、IDF、TF-IDF

<figure><img src="../../.gitbook/assets/image (259).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (260).png" alt=""><figcaption></figcaption></figure>

## <mark style="color:red;">例题</mark>：用term weighting schemes表示doc

<figure><img src="../../.gitbook/assets/image (262).png" alt=""><figcaption></figcaption></figure>
