# Dimensionality Reduction

高维数据在数据处理中会遇到[#common-pitfall-ren-zhi-xian-jing](./#common-pitfall-ren-zhi-xian-jing "mention")的问题，随着维度的增加效果变差。高维数据处理是具有挑战性的，并且在多数场景下是非必要的。所以在可视化中，常用的做法是：重新训练一个映射函数，通过特征组合进行降维。

High dimensionality is challenging and sometimes redundant. It is natural to try to reduce dimensionality to visualize. Reduce dimensionality by feature combination. Ideally, the new vector y should retrain from x all information important for learning.&#x20;

<figure><img src="../../.gitbook/assets/image (317).png" alt=""><figcaption></figcaption></figure>

*   PCA更看重全局数据的恢复

    PCA preserves the <mark style="color:red;">global shape/structure</mark> of the data
*   t-SNE更关注部分变量的区分性

    t-SNE preserves the <mark style="color:red;">local structure</mark>

## PCA（Principle Component Analysis）

[https://www.youtube.com/watch?v=nbBvuuNVfco\&list=RDCMUCm5mt-A4w61lknZ9lCsZtBw\&index=2](https://www.youtube.com/watch?v=nbBvuuNVfco\&list=RDCMUCm5mt-A4w61lknZ9lCsZtBw\&index=2)

[https://www.youtube.com/watch?v=fkf4IBRSeEc](https://www.youtube.com/watch?v=fkf4IBRSeEc)\
&#x20;by Steve Brunton, University of Washington, USA

### Main Idea

*   在低维空间找到最准确的数据表征形式

    seek the most accurate data representation in a lower dimensional space

### 数据预处理 Preprocessing

需要做median-maximum-minimum- normalization处理，转换成<mark style="color:red;">和均值的差值的归一化</mark>。

$$
\mu=\frac 1 {m} \sum_{i=1}^m {x_j^{(i)}} \\
 x_j^{(i)} = (x_j^{(i)} - \mu_j)/(x^j_{max} - x^j_{min})
$$

### 输入：协方差矩阵

由于数据上已经进行预处理，变成和均值的差的归一化。所以计算协方差矩阵的时候能够更便捷。

$$
\Sigma = \frac 1 m \sum_{i=1}^m (x^{(i)})(x^{(i)})^T
$$

### 输出：

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### 选取k个

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## t-SNE（t-distributed Stochastic Neighbor Embedding）

## Main Idea

将数据映射到一个维度，这个维度中的距离能够反映节点的相似度。

*   Step 1

    calculate the Euclidean distance from all the other points
*   Step 2

    transforms them into conditional probability that represents the similarity between two points

<figure><img src="../../.gitbook/assets/image (318).png" alt=""><figcaption></figcaption></figure>

### Step 1： High-dimensional space: how to compute the probability table
