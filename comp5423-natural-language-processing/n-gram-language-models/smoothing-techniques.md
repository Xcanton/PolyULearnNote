# Smoothing Techniques

## 数据稀疏性问题（Data Sparseness Problem）

当我们希望通过Tri-Gram甚至是Bi-Gram模型构造语言模型时，我们会发现有些Tri-grams甚至是bi-grams在训练集语料（corpus）从未出现过。这就会导致它的预测概率是0，

$$
P(w_k|w_{k-2},w_{k-1})=\frac {c(w_{k-2}, w_{k-1}, w_k)}{c(w_{k-2}, w_{k-1})}=0
$$

为了避免语言模型将未见过的事务分配0概率（而不是正确的概率），我们需要从频繁的事务中抽取部分脉率作为未见过的概率。（To keep a language model from assigning zero probability to these unseen events, we’ll have to shave off a bit of probability mass from some more frequent events and give it to the events we’ve never seen.）

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

同样的，我们也可以采取平滑的方式对概率进行优化。

## Smoothing（平滑）

原本对概率估计（以下以Uni-gram举例），有许多措施使未见过的组合概率值不为0。原始的极大似然概率为：

$$
P(w_k)=\frac {c(w_k)} {N}
$$

* N是训练语料中的词的总数（非词表数量）

### 拉普拉斯平滑Add-One（Laplace）Smoothing

本质上就是将各term加上1，使得未见过的词为1不为0。则总数增多了词表中词汇的数量（词表长度）。

$$
P^*(w_k)=\frac {c(w_k)+1} {N+V}
$$

$$
P^*(w_k|w_{k-1})=\frac {c(w_{k-1},w_k)+1} {c(w_{k-1})+V}
$$

* N是训练语料中的词的总数（非词表数量）
* V是词表长度

