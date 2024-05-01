# N-Grams

## 语言模型（Language Models，LM）

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

本质上语言模型就是计算一段词序列的概率或者下一个词的概率。

$$
P(w_1,w_2,\cdots,w_n)=P(w_1^n)
$$

如果用链式法则，那么这个概率的概率等于：<mark style="color:red;">条件概率的连乘</mark>

$$
P(w_1^n)=p(w1)p(w_2|w_1)p(w_3|w_1^2)\cdots p(w_n|w_1^{n-1})= \prod^n_{k=1}p(w_k|w_1^{k-1})
$$

## N-Gram Models

<mark style="color:red;">假设</mark>（<mark style="color:red;">马尔可夫假设</mark>，<mark style="color:red;">Markov assumption</mark>）：这个词的概率只跟前一个或几个词有关（the probability of a word depends only on the previous word(s)）。

由于我们没有办法也没有足够的语料获取真实的条件概率分布，所以出现了N-Gram模型，只跟前N-1个的条件有关（即一个词条是N个单词组成）。

$$
P(w_1^n) = \prod^n_{k=1}P(w_k|w_k-1),\ BiGram
$$

$$
P(w_k|w_{k-1}) = \frac {count(w_{k-1}, w_k)}{count(w_{k-1})}
$$

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

在一个Bi-Gram模型里面，连乘概率用上一个词预估下一个词的概率计算，通常会加上开头和结尾的统计概率。

而一个Tri-Gram模型，就是从上两个词预测下一个词。

## <mark style="color:red;">例题</mark>：计算句子概率

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

## 语言模型的评估指标

### 困惑度（Perplexity）

$$
PP(W) = \sqrt[N]{\frac 1 {P(w_1, w_2, \cdots, w_N)}}
$$



困惑度是用测试集的逆概率、再对句子词数量开方来评估句子效果。更低的困惑度意味着更高的句子概率，也就意味着更好的模型。

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
