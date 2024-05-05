# Dimensionality Reduction

高维数据在数据处理中会遇到[#common-pitfall-ren-zhi-xian-jing](./#common-pitfall-ren-zhi-xian-jing "mention")的问题，随着维度的增加效果变差。高维数据处理是具有挑战性的，并且在多数场景下是非必要的。所以在可视化中，常用的做法是：重新训练一个映射函数，通过特征组合进行降维。

High dimensionality is challenging and sometimes redundant. It is natural to try to reduce dimensionality to visualize. Reduce dimensionality by feature combination. Ideally, the new vector y should retrain from x all information important for learning.&#x20;

<figure><img src="../../.gitbook/assets/image (317).png" alt=""><figcaption></figcaption></figure>

## PCA（Principle Component Analysis）

[https://www.youtube.com/watch?v=nbBvuuNVfco\&list=RDCMUCm5mt-A4w61lknZ9lCsZtBw\&index=2](https://www.youtube.com/watch?v=nbBvuuNVfco\&list=RDCMUCm5mt-A4w61lknZ9lCsZtBw\&index=2)

[https://www.youtube.com/watch?v=fkf4IBRSeEc](https://www.youtube.com/watch?v=fkf4IBRSeEc)\
&#x20;by Steve Brunton, University of Washington, USA

### Main Idea

*   在低维空间找到最准确的数据表征形式

    seek the most accurate data representation in a lower dimensional space

### 数据预处理 Preprocessing

需要做median-maximum-minimum- normalization处理，转换成<mark style="color:red;">和均值的插值的归一化</mark>。

$$
\mu=\frac 1 {m} \
$$

### 输入：协方差矩阵

由于数据上已经进行预处理，变成
