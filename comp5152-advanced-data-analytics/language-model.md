# Language Model



*   收集一个大的语料数据集

    Get a big corpus of text which is a sequence of words
*   投喂进模型，并且计算下一个时间步的词分布

    Feed into Language Models, compute output distribution for every step T
* 计算输出和真实下一个词的交叉熵损失
* 损失函数其实是求解所有时间步的连乘，通过log变换转换为累加

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

如果计算整个语料库的自回归的话，计算开销巨大。所以实践中我们采用句子维度的方式，通过随机梯度下降从小chunk中更新模型。

## Evaluating Language Models

### 困惑度 Perplexity

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

很有意思的是，困惑度就等于交叉熵损失

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

## RNN-LM

## Machine Translation

### Statistical Machine Translation (SMT)

Machine Translation (MT) is the task of translating a sentence x from one language (the source language) to a sentence y in another language (the target language)

* 1950s: Russian to English, motivated by the Cold War
  * rule-based
* 1990s-2010s: Statistical Machine Translation
  * Probabilistic model
  * Bayes Rule- break this down into two components to be learnt separately
    * P(x|y): Translation Model
    * P(y): Language Model
  * Hundreds of important details we haven't mentioned here
  * Systems had many separately-designed subcomponents
  * Lots of feature engineering
  * Require compiling and maintaining extra resources
  * Lots of human effort to maintain

#### Decoding for SMT (Heuristic search algorithm)

$$
argmax_y\ P(x|y) P(y)
$$

### Neural Machine Translation (NMT)

最早的NMT是2014年，通过两个RNN网络进行的seq2seq网络。

Seq2Seq的任务模式可以使用在多种任务中：

* Summarization
* Dialogue
* Parsing
* Code generation

端到端训练，自回归的方式修正参数

#### Greedy Decoding

Greedy decoding is to take the most probable word on each step.&#x20;

<mark style="color:red;">Problem</mark>: No way to undo decisions. （老师认为的）

#### Exhaustive Search Decoding

穷举所有可能，很扯淡。

#### Beam Search Decoding

Not guaranteed to find optimal solution

But much more efficient than exhaustive search

Stopping Criterion:

* produces \<END>（但实际上跟模型有关，并且通常是\<eos>）
* 达到预设的cutoff

### <mark style="color:red;">NMT的好处</mark> Advantage of NMT

1. 翻译效果更好 Better performance
   1. 更流利 More fluent
   2. 语料运用更充分 Better use of context
   3. 更好计算词组的相似度 Better use of phrases similarities
2.  端到端训练，不需要额外训练组件

    can be trained end-to-end, with no subcomponents to be individually optimized
3.  需要更少的特征工程

    Requires much less human engineering effort

    1. No feature engineering
    2. Same methods for all language pairs

### <mark style="color:red;">NMT的坏处</mark> Disadvantages of NMT

1.  可解释性较差

    NMT is less interpretable
2.  难以控制，无法显式注入规则

    NMT is difficult to control, can't easily specify rules or guidelines for translation

### Machine Translation Evaluation

#### BLEU

### <mark style="color:red;">Challenge for NMT</mark>

* Out-of-vocabulary words
* Domain mismatch between train and test data
* Maintaining context over longer text
* Low-resource language pairs

## Attention

核心思想：在解码器上，只用编码器输出的特定部分向量直接连接（老师臆想的）

<figure><img src="../.gitbook/assets/image (331).png" alt=""><figcaption></figcaption></figure>

### Attention机制用在机器翻译上的好处

1.  显著提升机器翻译的性能

    Attention significantly improves NMT performance

    1. It's very useful to allow the decoder to focus on certain parts of the source
2.  为神经网络提供了类人的思考过程

    Attention provides a more "human-like" model of the MT process

    1. You can look back at the source sentence while translating, rather than needing to remember it all
3.  解决了长序列依赖的瓶颈问题

    Attention solves the bottleneck problem, allows the decoder to look directly at source
4.  提供了很多可解释性的空间

    Attention provides some interpretability

    1. By inspecting attention distribution, we can see what the decoder was focus on&#x20;
    2. Soft alignment for free
