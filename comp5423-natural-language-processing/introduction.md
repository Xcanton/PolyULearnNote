# Introduction

## NLP的任务

人类语言和计算机语言是两种不同的通信形式，具有不同的目的。虽然编程语言比人类语言简单的多，但没有太多语法，主要是词序和拼写。

自然语言处理的两大基础任务（Two fundamental Tasks）：

* 语言理解（Natural Language Understanding）
* 文本生成（Natural Language Generation）

由这两个基本的功能出发，派生了很多不同的NLP任务：

<figure><img src="../.gitbook/assets/image (236).png" alt=""><figcaption><p>Task in NLP</p></figcaption></figure>

* **Tokenization/ Segmentation**：给定一段文本，分成一段词序列（a sequence of word tokens）
* **Lemmatization/Stemming**：`词形还原`（Lemmatization）是将单词从屈折形式（inflectional forms）（表面形式，surface form）和其他派生形式（derivationally related forms）还原成基本形式。`词干提取`是词法分析的简单版本，它只简单地去除词缀。
* **Part-of-Speech Tagging**：`词性`（Part-of-Speech, POS）是一组具有相似语法功能的词的名称（the name for a group words, which have similar grammatical functions）（例如：名词noun、动词verb、代词pronoun、介词proposition、副词adverb、连接词conjunction等）。`词性标注`（POS Tagging）是为句子中每个单词分配词性的任务。
* **Syntactic Parsing**：`句法分析`（Syntactic Parsing）为句子分配句法结构。`成分分析`（Constituency parsing）注重于短语结构。
* **Chunking/Shallow (Partial) Parsing**：`分块`（Chunking）是为了识别句子中不重叠的片段（Chunking is to identify the non-overlapping segments of a sentence），例如：名字短语、形容词短语和介词短语。
* **Word Sense Disambiguation**：大多数单词有许多不同的含义。`词义消岐`（Word Sense Disambiguation，WSD）是一项确定特定上下文中使用的词义的任务。
* **Semantic Role Labeling**：`语义角色标注`（Semantic Role Labeling）是句子中的跨度分配角色任务（the task of assigning roles to spans in sentences）。例如：谓语、施事者（agent）、受事者（patient）、时间、地点和工具等。
* **Abstract Meaning Representation (AMR) Parsing**：`抽象意义表示`（AMR）是一种寓意表示语言。AMR图事有根有向非循环图（DAG）（rooted, labeled, directed, acyclic graphs），由整个句子组成。
* **Co-Reference Resolution**：`共指解析`（Co-Reference Resolution）是确定两个提到的实体是否是同一个等任务。在信息提取（Information Extraction, IE）中，命名实体是现实世界的对象（人、地点、组织、产品等），可以用适当的名称来表示。
* **Discourse Coherence**：连贯的文本（Discourse Coherence）是由文本单元之间存在的连贯关系构成的，例如修辞结构理论（Rhetorical Structure Theory, RST）。给定一个句子序列，自动确定基本话语单元（Elementary Discourse Units, EDU）之间的连贯关系的任务成为RST Parsing。

### Natural Language Understanding（自然语言理解）Task

NLU任务模拟人类是如何阅读的（NLU simulates how human read）

#### 语法（Morphological/Lexical）分析（Analysis）

词法分析关注的是单词是如何由语素（Morphological）构成的。

**KeyConcepts**： Tokenization, Stemming/Lemmatization, Chinese Word Segmentation

#### 句法分析（Syntactic Analysis）

句法分析关注如何将单词组合在一起形成正确的句子，并决定每一个单词在句子中扮演什么样的构成角色（Determines what structural role each word plays in the sentence），以及哪些短语是其他短句的子部分。

**KeyConcepts**： Part-of-Speech (POS) Tagging, Syntactic Parsing (构词分析Constituency Parsing, 依存关系分析Dependency Parsing), Chunking, Context-Free Grammar (aka. Phrase-Structure Grammar)

#### 语义分析（Semantic Analysis）

语义知识包含：单词在这个句子中是什么意思、这些意思怎么组成句子的含义（how these meanings combine in sentences to form sentence meanings）

**KeyConcepts**： 语义消岐Word Sense Disambiguation, Word Embedding, Semantic Role Labeling, Frame Semantic Parsing, Abstract Meaning Representation, First Order Logic (aka. Predicate Calculus)

#### 语篇分析（Discourse Analysis）

语篇（Discourse）关注的是前一句话如何影响下一句话。

**KeyConcepts**： Co-Reference Resolution, Discourse Coherence

### Natural Language Generation（自然文本生成）Task

NLG任务模拟人类是如何写作的（NLG simulates how human write）

#### 短语结构语法（Context-Free Grammar, aka. Phrase-Structure Grammar）

短语结构语法是自然语言中使用最广泛的构成结构模型系统（the most widely used formal system for modeling constituent structure in natural languages）

*   词汇（Lexicon）

    词汇包含单词（Word, such as fly, Sunday）、句法符号（Syntactic Symbols, such as 名词Noun、名词短语Noun Phrase, NP）
*   规则（Rules or Productions）

    每一种规则都表达了语言中的单词和符号可以分组和排列在一起的方式。（Each expresses the ways that words and symbols of the language can be <mark style="color:red;">grouped</mark> and <mark style="color:red;">ordered</mark> together.）

一个CFG可以从两种方式来看：

* 看成是给一个既定的句子指派结构（As a device for assigning a structure to a given sentence）
* 看成是生成句子（As a device for generating sentences）

#### 基于模版（Template based Geneartion）、模式识别（Pattern Recognition）和规则转换（Transformation Rules）的文本生成

#### 基于统计模型（Statistical (N-Gram) Model）或神经网络（Neural Language Model）的文本生成

逐字生成（Word-by-Word Generation）

### 文本纠缠（Textual Entailment, TE）和自然语言推理（Natural Language Inference, NLI）

| Premise                                                            | Label         | Hypothesis                                                         |
| ------------------------------------------------------------------ | ------------- | ------------------------------------------------------------------ |
| A man inspects the uniform of a figure in some East Asian country. | Contradiction | The man is sleeping.                                               |
| An older and younger man smiling.                                  | Neutral       | Two men are smiling and laughing at the cats playing on the floor. |
| A soccer game with multiple males playing.                         | Entailment    | Some men are playing a sport.                                      |

## NLP的技术（算法）类别

### 文本分类（Text Classification）

<figure><img src="../.gitbook/assets/image (237).png" alt=""><figcaption></figcaption></figure>

分类内容包括多种，其中情感分类（Sentiment/Emotion Classification）、垃圾邮件（Email Spam Detection）、虚假新闻分类（Fake News Detection）等都是主流

### 文本排序（Text Ranking）

<figure><img src="../.gitbook/assets/image (239).png" alt=""><figcaption></figcaption></figure>

主要内容包括信息检索（Information Retrieval）、总结提取（Extractive Summarization）、基于检索的对话系统（Retrieval-based Dialogue Systems）

### 信息提取（Information Extraction）/序列标注（Sequence Labeling）

<figure><img src="../.gitbook/assets/image (238).png" alt=""><figcaption></figcaption></figure>

主要包括：问答（Question Answering）和知识推理（Knowledge Discovery）

### Sequence-to-Sequence Generation

<figure><img src="../.gitbook/assets/image (240).png" alt=""><figcaption></figcaption></figure>

## NLP的历史

<figure><img src="../.gitbook/assets/image (241).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (242).png" alt=""><figcaption></figcaption></figure>

### LLM的历史

<figure><img src="../.gitbook/assets/image (243).png" alt=""><figcaption></figcaption></figure>

## NLP的挑战

最大的问题是：语言的灵活性（Language is Flexible），没有固定的词汇（Open-ended Vocabulary），灵活的组合（Flexible Combination）和变化的语法（No Fixed Grammar）。

语言的模糊体现在各个层级（Language is Ambiguity at Different Levels）：

* Word-Level（一词多义）
* Word Segmentation Level（断句）
* Sentence-Level Syntactic（with指代不明）
* Coreference Ambiguity（代词指代不明，多名称实体）
