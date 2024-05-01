# Advanced Frame-based Approach

## Dialogue-State/Belief-State Architecture

<figure><img src="../../../.gitbook/assets/image (292).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (293).png" alt=""><figcaption></figcaption></figure>

## Dialogue State Tracking

Dialogue state不仅包含了当前句子提取的slot值，还包含了到现在所有的状态、所有的用户约束（It also includes the entire state of the frame at this point, summarizing all of the user's constraints）

<figure><img src="../../../.gitbook/assets/image (294).png" alt=""><figcaption></figcaption></figure>

由于dialogue act包含了对slots的限制和取值，所以对dialogue act detection的多分类和slot- filling的Sequence Labeling可以一起实现。（Since dialogue acts places some constraints on the slots and values, the tasks of dialogue act detection and slot-filling can be performed jointly）

## Dialogue Policy Learning

Dialogue Policy限制的目的是：决定系统应该采取什么回复，即生成什么对话内容。（what action the system should take next, that is, what dialogue act to generate）

因为对话不是独立的，而是有结构的：

* Question & Answers
* Proposal & Acceptance/Rejection
* Greeting & Greeting
* etc

### Approaches

*   Supervised Learning Approaches

    <figure><img src="../../../.gitbook/assets/image (295).png" alt=""><figcaption></figcaption></figure>
*   Reinforcement Learning Approaches

    * Markov Decision Process

    <figure><img src="../../../.gitbook/assets/image (296).png" alt=""><figcaption></figcaption></figure>

## Natural Language Generation

传统的NLG包含两个stage：

* content planning（what to say）
  * Content planning is generally done by the dialogue policy, which has chosen the dialogue act to generate.
* sentence realization（how to say it）

### Approaches

*   Template-based Generation



    <figure><img src="../../../.gitbook/assets/image (297).png" alt=""><figcaption></figcaption></figure>
* NN-based Generation

## Challenges &  Research Focuses

* Dialogue Planning：Reactive vs. Proactive Dialogue
  * effective dialogue planning is essential for goal-oriented dialogue
* Domain Transfer for NLU and Domain State Transfer
* Training Environment for Policy Learning
* End2End system vs Modular Systems

## Conversational Question Answering

Conversation History as Context：与单纯提问回答不同的是，Conversation Context可能在之前的History出现。（Utilize the conversation context to reformulate the current question or refine its representation(context-enhanced question representation)）

解决方案也有两种：

*   将问题都拼接起来



    <figure><img src="../../../.gitbook/assets/image (298).png" alt=""><figcaption></figcaption></figure>
*   将问题重写



    <figure><img src="../../../.gitbook/assets/image (299).png" alt=""><figcaption></figcaption></figure>
