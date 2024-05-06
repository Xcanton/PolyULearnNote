# Word Semantic Representations

## One-hot Representations

<figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>

不好：没有反映出词间距离，且词向量大

**Word Semantics（Meaning）**

* Synonymy（同义词）
  * Love/Like, Couch/Sofa
* Words with Similar Meanings（近义词）
  * Coffee/Tea（both are beverages）
  * Cat/Dog（both belong to the same family of animals）
  * Car/Bicycle（both are means of transportation）
* Words Related（相关的词）
  * Coffee/Cup， Pen/Paper

## Sparse Vectors and Dense Vectors

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

两个假设：

1.  词是由语言中的分布决定的，即它附近的单词和语法环境

    The meaning of a word is defined by its distribution in the language, meaning its neighboring words or grammatical environments
2.  在相似语法结构出现的词具有相似的意思

    Words that occur in similar contexts tend to have similar meanings

相近词的Embeddings在<mark style="color:red;">Semantic Space</mark>具有距离接近的性质

### Co-occurrence Matrix

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

相近的词在文档中出现的分布相近

## [#li-ti-ji-suan-liang-ge-embedding-de-xiang-si-du](./#li-ti-ji-suan-liang-ge-embedding-de-xiang-si-du "mention")

