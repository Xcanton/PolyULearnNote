# Simple Frame-based Approach

<figure><img src="../../../.gitbook/assets/image (283).png" alt=""><figcaption></figcaption></figure>

## Domain Knowledge

简而言之，就是为特定的场景设定了需要的资料，并且针对缺少的资料通过问答的方式填充。

<figure><img src="../../../.gitbook/assets/image (284).png" alt=""><figcaption></figcaption></figure>

对于不同的slots，有预先设定好的问题集。对于缺省的slot，从预设的问题集中抽取问题进行询问。

## Rule-based Dialogue Management

### Dialogue Management （DM）

The DM module is responsible for the state and flow of the conversation

* Dialogue State Tracking
* Dialogue Policy

### Dialogue Flow Control

<figure><img src="../../../.gitbook/assets/image (286).png" alt=""><figcaption></figcaption></figure>

如果一个回复包含了multiple slots，系统需要针对性得填充所有相关的slots，并且跳过已经填充的相关slots问题，继续询问remaining slots。

一个对话系统可能包含多个frames，所以需要在frames switch的时候保留对应的信息。

## NLU Modules

<figure><img src="../../../.gitbook/assets/image (287).png" alt=""><figcaption></figcaption></figure>

三个阶段（顺序）：

* domain identification（<mark style="color:red;">Classification</mark>）
* intent detection（<mark style="color:red;">Classification</mark>）
* slot filling（<mark style="color:red;">Information Extraction</mark> -> <mark style="color:red;">Sequence Tagging</mark>）

<figure><img src="../../../.gitbook/assets/image (288).png" alt=""><figcaption></figcaption></figure>

在Domain和Intent Classification中常用的方案：

* **Conventional ML-based Approaches**
  *   Classifier&#x20;

      LR、SVM、Decision Tree、Random Forest、CNN
  *   Feature

      word N-Grams

在Slot Filling （Sequence Labeling）中常用的方式：

* **Conventional ML- based Approaches**
  *

      <figure><img src="../../../.gitbook/assets/image (289).png" alt=""><figcaption></figcaption></figure>


  *   Sequence Models

      Maximum Entropy Markov Model（<mark style="color:red;">MEMM</mark>）、Conditional Random Field（<mark style="color:red;">CRF</mark>）、RNN
  *   Features

      Word N-Grams、Lexicons（例如预设的机场名称、星期几）
*   **Modern NN-based Approaches**

    <figure><img src="../../../.gitbook/assets/image (290).png" alt=""><figcaption></figcaption></figure>


* **Rule-based Approaches**
* **Template-based Approaches**
*   **Linguistics-based Approaches**

    <figure><img src="../../../.gitbook/assets/image (291).png" alt=""><figcaption></figcaption></figure>



