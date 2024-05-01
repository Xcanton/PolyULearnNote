# Retrieval-based Approaches

## Copy the most relevant context from human2human conversation dataset

Principle原理：

* 在既定的数据集中，通过召回和复制最合适的回复，回复用户的输入
* is to respond to a user's turn (denoted as a query <mark style="color:red;">q</mark>) by retrieving and copying the <mark style="color:red;">appropriate turn</mark> (<mark style="color:red;">r</mark>) from a human conversation dataset (<mark style="color:red;">C</mark>).

## Retrieval的方式

主要的方式分成两种，通俗的讲就是：

*   召回最相关的问题，然后返回他的回答

    Looking for the most resembles相似的 user's turn, and return the response to that turn.
*   直接召回最相关的答案（实验证明最好）

    Directly match the user turn with the turn having the highest score from the corpus

由于基础的数据集中，是人人对话，假设两个人对话，那么A可以作为system，B也可以作为system。

<figure><img src="../../../.gitbook/assets/image (280).png" alt=""><figcaption></figcaption></figure>
