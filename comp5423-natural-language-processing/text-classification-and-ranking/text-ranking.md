---
description: Relevance&Cosine Similarity、BAg-of-Word Retrieval vs. Dense Retrieval
---

# Text Ranking

## 文本相似度（Text Similarity）

<figure><img src="../../.gitbook/assets/image (268).png" alt=""><figcaption></figcaption></figure>

查询文本在搜索系统中被当成短文本对待。本质上的排序就是计算文档跟查询文本的相似度（可能是sim或模型评估）。

$$
\mathop{d}\limits ^{\rightarrow}=(d_1, d_2, \cdots, d_n)\\
\mathop{q}\limits ^{\rightarrow}=(q_1, q_2, \cdots, q_n)
$$

### 欧式距离相似度（Euclidean Length of a Vector）



$$
|\mathop{d}\limits ^{\rightarrow}| = \sqrt{\sum^n_{i=1} {d_i}^2}
$$

### 点积相似度（Dot Product）

$$
\mathop{d}\limits ^{\rightarrow} \cdot \mathop{p}\limits ^{\rightarrow}=\sum^n_{i=1} {d_i p_i}
$$

### 余弦相似度（Cosine Similarity）

$$
\cos{(\mathop{d}\limits ^{\rightarrow}, \mathop{p}\limits ^{\rightarrow})} = \frac {\sum d_ip_i} {\sqrt {\sum {d_i}^2}\sqrt {\sum {p_i}^2}}\\
=\frac {\mathop{d}\limits ^{\rightarrow} \cdot \mathop{p}\limits ^{\rightarrow}}{|\mathop{d}\limits ^{\rightarrow}| \times |\mathop{p}\limits ^{\rightarrow}|}
$$

## <mark style="color:red;">例题</mark>：根据query计算文档排序

<figure><img src="../../.gitbook/assets/image (269).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (270).png" alt=""><figcaption></figcaption></figure>

## 检索系统的工业部署

<figure><img src="../../.gitbook/assets/image (272).png" alt=""><figcaption></figcaption></figure>

工业上可以将词条对应的文档用Inverted Index File存储起来，也可能是链表。实际检索的时候只需要遍历链表就行。事实上链表头还可以存词频。

<figure><img src="../../.gitbook/assets/image (274).png" alt=""><figcaption></figcaption></figure>

## Dense Retrieval

<figure><img src="../../.gitbook/assets/image (271).png" alt=""><figcaption></figcaption></figure>

本质上就是将Sparse的特征向量映射到低维空间，变成稠密的向量。
