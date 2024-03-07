---
description: Stemming（词干提取） and Lemmatization（词形还原）
---

# Morphological Analysis

## 语素（Morphological）

语素（<mark style="color:red;">Morphological</mark>）分析是研究单词是如何构成的，就是小的语义单元（smaller meaning-bearing units）。

语素可以分为两个宽泛的大类：

*   词干（stems）

    词干（stems）是单词的主要语素，提供主要含义（supplying the main meaning）。
*   词缀（affixes）

    词缀（affixes）添加各种附加的含义（add additional meaning of various kind）。

词干提取（Stemming）和词形还原（Lemmatization）属于词法分析。

英语通过前缀和后缀来表达屈折（<mark style="color:red;">inflectional</mark>）和派生（<mark style="color:red;">derivational</mark>）形态。

### 屈折形态（inflectional）

屈折形态是相对简单一些，是由复数（number agreement， -s）和时态标记（tense markings， -ed和-ing）组成。

### 派生形态（derivational）

派生形态更加复杂，包含多种后缀（suffixes, e.g., -tion, -ness, -able）和前缀（prefixes， e.g., co-, re-）。

这种后缀词缀通常适用于同一类单词，将其变回原形也可以用统一的方式：

* adjective-to-noun：-ness（slow➡️slowness）
* adjective-to-verb：-ly（personal➡️personally）
* noun-to-adjective：-al（recreation➡️recreational）
* noun-to-verb：-fy（glory➡️glorify）
* verb-to-adjective：-able（drink➡️drinkable）
* ……

## 词形还原（Lemmatization）

<figure><img src="../../.gitbook/assets/image (250).png" alt=""><figcaption></figcaption></figure>

词形还原（<mark style="color:red;">Lemmatization</mark>）是将单词的屈折形式（<mark style="color:red;">inflectional</mark>）和部分派生形式（<mark style="color:red;">derivational</mark>）还原成简单形式或词条（<mark style="color:red;">Lemma</mark>）。一个词条（Lemma）是单词的规范形式或字典形式（A lemma is the canonical form or dictionary form of a word.）。

## 词干提取（Stemming）

<figure><img src="../../.gitbook/assets/image (251).png" alt=""><figcaption></figcaption></figure>

词干提取（Stemming）是语素分析的简单形式（is a naive version of morphological），因为它直接把后缀全删掉（which simply strip off affixes）。词干提取比较适用在不需要语素结构的应用场景（像信息检索Information Retrieval）。

\*<mark style="color:red;">中文没有语素变形（Chinese is not a language with morphological variations）</mark>\*

## 中文的语素分析（Morphological Analysis for Chinese）

### Chinese Word Tokenization（Word Segmentation）

像中文这种词与词之间没有空格的文本，我们可以通过词语分割（word segmentation）的方式划分成词。词划分方式包括了：

* dictionary based
* statistical based
* machine learning based

### Dictionary-based Word Segmentation

基于词典的分词算法是通过匹配字符和词表中的单词实现分词的。成功匹配的字符换呗转化成一串词Token序列。

匹配的方向有：正向匹配（<mark style="color:red;">Forward Matching</mark>）和反向匹配（<mark style="color:red;">Backward Matching</mark>）

匹配长度的优先级有：最大长度优先（<mark style="color:red;">Maximum Matching</mark>）和最小长度优先（<mark style="color:red;">Minimum Matching</mark>）

从性能上来说，反向匹配的精度会更高。但是正向和反向都能达到95%以上的accuracy。

### 前向最大长度匹配（Forward Maximum Matching）

<figure><img src="../../.gitbook/assets/image (252).png" alt=""><figcaption><p>Forward Maximum Matching Algorithm</p></figcaption></figure>

简而言之，前向最大匹配就是在设定的最大长度（MaxLen）中，寻找词典中是否有一样的词。如果没有，则减少最后的字符重新检索字典，直到两个字符都不满足的时候，将剩下的字符作为单字符。如果从字典中找到了匹配的词，那么从下一未匹配的文本重新最大长度匹配。

#### 例题：前向最大长度匹配（Forward Maximum Matching）

<figure><img src="../../.gitbook/assets/image (253).png" alt=""><figcaption><p>Example of Forward Maximum Matching</p></figcaption></figure>

### 前向最小长度匹配（Forward Minimum Matching）

<figure><img src="../../.gitbook/assets/image (254).png" alt=""><figcaption></figcaption></figure>

简而言之，最小长度匹配是从两个字符开始，从词典中匹配。如果未匹配到词典中的词，那么加上一个字符再从词典中匹配，直到字符串结束或者达到预设的最大长度（MaxLen）。如果未匹配成功，则将第一个字符作为单字符词输出。一旦成功分词，那么将从下两个字符重新开始匹配。

#### 例题：前向最小长度匹配（Forward Minimum Matching）

<figure><img src="../../.gitbook/assets/image (255).png" alt=""><figcaption><p>Example of Forward Minimum Matching</p></figcaption></figure>

### 分词的不准确性（Ambiguity in Word Segmentation）

#### 90%：重叠分词模糊（Overlapping Ambiguity）

<figure><img src="../../.gitbook/assets/image (256).png" alt=""><figcaption></figcaption></figure>

重叠分词模糊的原因是：出现了连续字符串ABC，既可以被划分成A^BC，也可以被划分成AB^C。这种情况占据分词模糊中的绝大多数情况（90%）。

#### 10%：组合分词模糊（Grouping Ambiguity）

<figure><img src="../../.gitbook/assets/image (258).png" alt=""><figcaption></figcaption></figure>

组合分词模糊的原因是：出现了连续字符串AB，也存在A和B单独的词条。不过这种情况占少数（10%）。

## Sub-Word Segmentation (Sub-Word based Tokenization )

<figure><img src="../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>

由于语言是变化迅速的，所以难免遇到未知字符/陌生词组的情况。为了应对这种情况，可以采用子词（Sub-words）tokenization。所谓的子词（Sub-words），就是比词组更小的单元。（modern tokenizers often automatically induce sets of tokens that include tokens smaller than words, called sub-words, from corpus.）

这种子词的组合，是可以从语料（<mark style="color:red;">corpus</mark>）中学习到的。

### Byte-Pair Encoding (BPE) Algorithm

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption><p>pseudocode for BPE</p></figcaption></figure>

BPE算法就是一种从语料中学习Sub-Word的算法。简单来说，BPE算法先将所有的字符单独作为token放在语料库中，然后开始迭代：从词表统计中挑选出出现次数最多的两个组合（所以叫Byte-Pair），然后更新到词表中，再更新语料，如果新的token：AB能够覆盖所有B或A的情况，那就把B或A从统计中删除。重复迭代直到压缩率达标。

<mark style="color:red;">迭代后的子词可以是模糊含义的子字符串，也可以是具有明确意义的语素单元</mark>（Sub-words can be arbitrary substrings, or they can be meaning-bearing units like the morphemes）

#### 例题：BPE算法迭代Tokenizer

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

