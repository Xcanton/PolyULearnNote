---
description: Classification Models、Linguistic Features
---

# Text Classification

## 文本分类模型（Classification Models）

文本分类可能是二分类任务，也可能是多分类任务。

* 常见的二分类任务（Binary Classification）
  *   情感分类（Sentiment Classification）

      判断作者对某个物体的情感倾向是正向的还是负向的
  *   垃圾邮件判断（Email Spam Detection）

      检测收到的邮件是不是垃圾邮件
* 常见的多分类任务（Multi-Class Classification）
  *   新闻类别判断（News Categorization）

      判别一个新闻的主题（商业的、科技的、企业的等）

常见的分类模型（Classification Models）

贝叶斯模型（Naive Bayes, NB）、逻辑回归（Logistic Regression，LR）、支持向量机（SVM）、随机森林、CNN（Convolutional Neural Networks）、BERT等

生成式模型（Generative Model）：[Chapter 4](https://web.stanford.edu/\~jurafsky/slp3/4.pdf)

判别模型（Discriminative Model）：[Chapter 5](https://web.stanford.edu/\~jurafsky/slp3/5.pdf)

## 分类特征（Classification Features）

和其他有监督等机器学习模型一样，文本分类是一系列有效特征等特征工程过程。

常见的分类特征有：

* 浅层特征（Surface Text Features）
* 基于情感词典等特征（Lexicon-based Features）
* 语言特征（Linguistic Features）
* 其他统计特征和细粒度特征（Other Statistic and Specially Designed Features）

### 浅层特征（Surface Text Features）

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

浅层特征是（基于TF或TF-IDF Weighted的）N元词向量（Word N-Grams），例如：一元词特征（Uni-gram Features）、二元词特征（Bi-Gram Features）等。

### 基于情感词典等特征（Lexicon-based Features）

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

也是基于词向量的特征（Sentiment Words and Phrases），不过目标词向量换成了情感词典中的词向量（From Sentiment Lexicon/Dictionary）。

常用的情感词典有：

* [General Inquirer ](https://inquirer.sites.fas.harvard.edu/)(GI)
* [LIWC](http://tapor.ca/tools/249)
* [The Opinion Lexicon](https://www.cs.uic.edu/\~liub/FBS/sentiment-analysis.html) from HU and LIU
* [MPQA Subjectivity Lexicon](https://mpqa.cs.pitt.edu/lexicons/)

### 语言特征（Linguistic Features）

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

语言特征（Linguistic Features）包括POS（Part-of-Speech）Tags和他们的N-Gram特征（POS N-Grams Features）。

### 其他统计特征和细粒度特征（Other Statistic and Specially Designed Features）

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## 输入文本表征（Representation of Input Text）

输入文本的表征形式主要有以下两种：基于特征工程的、基于表征学习的

### 基于特征工程的输入表征（Feature Design）

这种情况下，特征通常是基于语言直觉（Linguistic intuitions）和该领域语言文献（Linguistic Literature on the domain），并基于训练集设计（generally designed by examining the training data set）的特征。

（Features are generally designed by examining the training data set with an eye to linguistic intuitions and the linguistic literature on the domain.）

### 基于表征学习的输入表征（Representation Learning）

<figure><img src="../../.gitbook/assets/image (5) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

为了避免在特征设计的时候引入大量的人工干预，近期的研究都聚焦到怎么用embedding在预训练到过程中提取向量表征。
