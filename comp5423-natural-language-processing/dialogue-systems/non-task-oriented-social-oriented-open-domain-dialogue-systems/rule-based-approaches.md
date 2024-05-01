# Rule-based Approaches

## Pattern Matching & Transformation Rules

## <mark style="color:red;">ELIZA</mark> pattern/rule

本质上是基于识别出的句型结构，根据回复模版给出回答。

* 根据关键词识别出可能出现的场景（可以一对多）
* linked to a keyword that might occur in a user sentence
* 关键词之间有排名，根据排名选择回复
* Keywords are associated with a rank, with specific words being more highly ranked, and more general words ranking lower

<figure><img src="../../../.gitbook/assets/image (278).png" alt=""><figcaption></figcaption></figure>

* 如果没有识别到关键词，那么会回复一个<mark style="color:red;">non-committal response</mark>，即默认兜底的回复逻辑（I see, please go on, that's very interesting）。
  *   或者从对话历史中选择一个（<mark style="color:red;">a clever memory tirck</mark>）

      识别一个跟I或者my有关的用户状态，存储进队列中。需要的时候获取一个最老的状态询问。模版是随机选择的。
  *

      <figure><img src="../../../.gitbook/assets/image (279).png" alt=""><figcaption></figcaption></figure>
