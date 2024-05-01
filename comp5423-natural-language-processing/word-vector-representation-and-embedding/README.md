# Word Vector Representation and Embedding

## 【<mark style="color:red;">例题</mark>】计算两个embedding的相似度

### 1. Cosine similarity in Term-Context Matrix



<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

### 2. Pointwise Mutual Information（PMI）

对两个词相关性衡量的最好方法是衡量在语料中，两个词同时出现的概率有多大（The best way to weight the association between two words is to ask how much more the two words co-occur in the corpus）

$$
PMI(w, c) = \log_2{\frac {P(w, c)} {P(w)P(c)}}
$$

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

简而言之，就是计算共现频率处以词频乘积的log值。但是会引发其他问题（语料中没有活或者少量的共现次数，会导致<mark style="color:red;">负数PMI</mark>）

### 3. Positive Pointwise Mutual Information（PPMI）

$$
PPMI(w, c) = \max(\log_2{\frac {P(w, c)} {P(w)P(c)}},0)
$$

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>
