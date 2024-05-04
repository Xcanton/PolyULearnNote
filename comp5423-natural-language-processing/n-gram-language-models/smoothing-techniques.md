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

### <mark style="color:red;">例题</mark>：计算拉普拉斯平滑

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

### 加K平滑Add-K Smoothing

$$
P^*(w_k|w_{k-1})=\frac {c(w_{k-1},w_k)+k} {c(w_{k-1})+kV}
$$

拉普拉斯平滑的一个变种，由增加1变成增加k，减少语料中出现少的词汇的误差。k通常取百分比（A Fractional Count），例如：0.5，0.05，0.01。

尽管加K平滑在某些任务上有效（包括文本分类任务），但是它<mark style="color:red;">在语言模型中效果不佳</mark>。

### 回退平滑（Backoff Smoothing）

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

如果在高阶N-Gram上概率为0，那么回退成低阶概率。

In backoff, we use the Tri-gram if the evidence is sufficient, otherwise we use the Bi-gram, otherwise the Uni-gram. In other words, we only “back off” to a lower-order N-gram if we have zero evidence for a higher-order N-gram.

#### Katz Backoff（一种回退算法，不重要）

<figure><img src="../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>

### 线性插值（Linear Interpolation）

相反的，我们可以通过线性插值的方式对0概率的部分平滑。

<figure><img src="../../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption></figcaption></figure>

经验证明，插值平滑方式效果更好。

## \<UNK>问题（OOV，Out of Vocabulary）

我们有两种处理方式：

1. 暴力从训练集中选择部分词作为\<unk>，然后一起训练概率
2. 不在训练集中处理，而是在推理时给\<unk>分配一个小概率。

需要注意的是：\<unk>会影响模型评判指标（例如困惑度Perplexity）。一个语言模型可以通过将少量词汇指定为\<unk>联合训练成unknown word，从而获得高的概率。

Note that the exact choice of model does have an effect on metrics like perplexity. A language model can achieve low perplexity by choosing a small vocabulary and assigning the unknown word a high probability.

所以训练和推理需要采用同一套词表。
