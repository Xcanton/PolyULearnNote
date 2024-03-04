---
description: Tokenization, Normalization and Segmentation
---

# Text Normalization(Pre-Processing)

## Sentence Segmentation划分句子

划分句子是nlp预处理的第一个部分（Sentence Segmentation is an important first step in text pre-processing）。最有用的技巧是通过标点符号（<mark style="color:red;">Punctuations</mark>）来划分句子：例如句号（<mark style="color:red;">periods</mark>）、问号（<mark style="color:red;">Question Marks</mark>）和感叹号（Exclamation Points）。

但是符号也会带来歧义：

1. 句子的边界有句号
2. 句子缩写Abbreviation（e.g., MR. or Inc.）
3. Number（e.g., 6.66%）

消歧是一项二分类任务（Disambiguation is a binary classification task.）。可以通过多种方式（算法）进行识别：

### Rule-based Classifiers

基于规则的算法最典型的要属[Stanford ](https://stanfordnlp.github.io/CoreNLP/)[CoreNLP](https://stanfordnlp.github.io/CoreNLP/)，该包中句子划分是基于规则的句子划分。以下是基于规则的句子划分的示例：

<figure><img src="../../.gitbook/assets/image (246).png" alt=""><figcaption></figcaption></figure>

### Learning-based Approaches

基于机器学习的句子划分可以采用统计特征等句子输入，再经过多种划分模型对当前是否应该断句判断二分类问题。

常用的Classifiers有：

* Decision Tree
* Naive Bayes
* SVM
* Logistic Regression

常用的统计特征有：

* Length of the word with "." 目前句子的长度
* Case of the word with "." 出现句号前的单词
* Probability of the word with "." that occurs at EOS 该词在结尾的概率

## Word Tokenization单词划分

tokenization任务是将给的的字符序列切分成单词块（<mark style="color:red;">word tokens</mark>），并可能丢弃部分字符（例如标点符号）。（Given a sequence of characters, tokenization is the task of chopping it up into pieces, called word tokens, perhaps at the same time throwing away certain characters, such as punctuations.）

<figure><img src="../../.gitbook/assets/image (247).png" alt=""><figcaption></figcaption></figure>

同样的，单词划分的标准也是模糊的。例如附着词、缩写、数字、日期、网站等都会带来歧义的划分。所以我们需要一套标准的划分规则（<mark style="color:red;">NLTK.regexp tokenize function</mark>就是个很好的选择）

<figure><img src="../../.gitbook/assets/image (248).png" alt=""><figcaption><p>NLTK Rules</p></figcaption></figure>

## Word Normalization单词标准化

单词标准化是将单词还原成标准的形式，从一个单词的多种变型中选择一个简单的形式。（Word normalization is the task of putting words/tokens in a standard format, choosing a single normal form for words with multiple forms.）

<figure><img src="../../.gitbook/assets/image (249).png" alt=""><figcaption></figcaption></figure>
