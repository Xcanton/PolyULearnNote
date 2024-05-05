# Dialogue Systems

根据应用方式，对话系统可以划分成两大类别：

* [task-oriented-domain-specific-dialogue-systems](task-oriented-domain-specific-dialogue-systems/ "mention")
  * 目的是assist the user to <mark style="color:red;">complete specific tasks</mark>
  * Conversational Question Answering and Conversational Recommendation
* [non-task-oriented-social-oriented-open-domain-dialogue-systems](non-task-oriented-social-oriented-open-domain-dialogue-systems/ "mention")
  * 根据与用户的交互过程，提供合理的回复和<mark style="color:red;">entertainment</mark>
  * interact with humans to provide reasonable responses and <mark style="color:red;">entertainment</mark>
  * 也被称为open-domain systems或者chit-chat dialogue system

还可以按照对话轮次进行划分，划分成单轮对话和多轮对话：

* 单论对话只在user和system间进行一次，通常是user输入一个information need 或者asks a question，系统回复相应的relevant information or an answer。然后对话结束了。
* 多轮对话允许用户基于previous questions and/or answers提出follow-up questions， 系统提供relevant responses。

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## 【<mark style="color:red;">vs</mark>】Generation-based vs Retrieval-based

*   检索系统通过从人类反应集中检索最相关的回复，能够在表层语义特征中更加连贯。

    select responses from human response sets and thus are able to achieve better <mark style="color:red;">coherence in surface-level language</mark>.
*   但是受限于语料库的质量，有时候会召回出相关性低的回复

    restricted by <mark style="color:red;">the finiteness of the response sets</mark> and sometimes the responses retrieved show a <mark style="color:red;">weak correlation</mark> with the dialogue context.
* 生成式的方式更加灵活(<mark style="color:red;">flexible</mark>)
*   但是有时候会缺乏连贯性，处于训练语料的安全或者常见回答的原因，产生低质量的回复。这类回复会导致对话终止

    sometimes they <mark style="color:red;">lack coherence</mark> and tend to produce safe, commonplace responses like IDK or I'm OK that shut down the conversation

## 【<mark style="color:red;">vs</mark>】Challenges & Research Focuses

*   <mark style="color:red;">Context Modeling</mark>（内容建模）

    Single turn vs multi turn dialogue

    * Both generation-based and retrieval-based <mark style="color:red;">rely heavily on dialogue context modeling</mark>
* <mark style="color:red;">Response Coherence</mark>（内容连贯性）
* <mark style="color:red;">Response Diversity</mark>: One2Many Mapping（回复多样性）
  * external knowledge是提升回复多样性的重要手段，因为它可以enrich内容
* <mark style="color:red;">Speaker Consistency</mark>（说话人一致性） and <mark style="color:red;">Personality-based Responses</mark>（个性化回复）
  * 对persona的Explicitly modeling显式建模是当前的主流方案
* <mark style="color:red;">Empathetic Responses</mark>（同理心回复）
  * 需要sense other people's feelings and produce appropriate response
