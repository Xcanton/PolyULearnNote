# Word Embeddings

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

## Skip-Gram（with Negative Sampling）

思想：不是计算共现概率，而是通过可训练的词向量，训练一个<mark style="color:red;">二分类</mark>的分类器，来分辨中间这个词出现在这个语段的概率。

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

通过Self-Supervision自监督的方式训练，并且对负样本做负采样。

*   Classifier

    Logistic Regression Classifier
* Training Processing
  * Treat the target word and a neighboring context word as positive samples
  * <mark style="color:red;">Randomly sample</mark> other words in the lexicon to get negative samples
  * train
  * use the learned weights as the embeddings

实际上在训练的时候，是通过对两两的相似度进行计算，并且连乘，得到是否分别的概率。并且通过交叉熵损失进行优化。

$$
P(+|w,c_i)=\frac 1 {1+ e^{-w*c_i}}
$$

$$
P(+|w,c_{1:L})= \prod \limits_{i=1}^L \frac 1 {1+ e^{-w*c_i}}
$$

$$
L(\theta)=\sum_{(t,c) \in +} {\log{P(+|w,c)}} + \sum_{(t,c) \in -} {\log {P(-|w,c)}}
$$

事实上，训练后的embedding具有良好的偏移性质，对共现的词概率较高，非共现的词概率较低。并且在一定程度上能够反映语意偏移（<mark style="color:red;">Relational Properties</mark>）的现象。

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

## Continues Bag-of-Words（CBOW）

对比：

* CBOW： <mark style="color:red;">Several times faster</mark> to train than Skip-Gram, <mark style="color:red;">slightly better accuracy for the frequent words</mark>
* Skip-Gram： Works well with a small amount of the training data, represents well even <mark style="color:red;">rare words or phrases</mark>
