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

