# Neural Language Model Architecture

## Pre-Trained LM

<figure><img src="../../.gitbook/assets/image (305).png" alt=""><figcaption></figcaption></figure>

## Bert（encoder only）

*   Masked Language Model

    15%的mask，其中80%是mask，10%是随机替换，10%是原词
*   Next Sentence Prediction

    <figure><img src="../../.gitbook/assets/image (306).png" alt=""><figcaption></figcaption></figure>

Variations: Roberta, Albert, SpanBert

## GPT（Decoder Only）

PreTraining task： Next Word Prediction

Task Adaptation

* Utilize Task-Specific Input Adaptation
* Train Parameters of an Added Linear Output Layer

<figure><img src="../../.gitbook/assets/image (307).png" alt=""><figcaption></figcaption></figure>

在计算两个句子相似度的任务时，需要将两个句子顺序交换，计算两次并相加，消除位置带来的差别。再过Linear层。

## GPT2(Dream)

是一个Unsupervised Model for Multi-Tasks（去除了Task-Specific Fine-tuning）

<figure><img src="../../.gitbook/assets/image (308).png" alt=""><figcaption></figcaption></figure>

加入了Task Instructions

<figure><img src="../../.gitbook/assets/image (309).png" alt=""><figcaption></figcaption></figure>

* 问答或选择类的任务在与Finetune的基线模型效果相近
* Generate类任务爆差

## GPT3：Auto-Regressive Language Model

### Prompt-based, In-Context Learning

Zero-shot、One-shot、Few-shot Learning

结论：大模型能够更有效地应用incontext information（Larger models make increasingly efficient use of in-context information）

<figure><img src="../../.gitbook/assets/image (310).png" alt=""><figcaption></figcaption></figure>

## InstructGPT

### Trained with Humans in the Loop

* Aligning Language Models to Follow Instructions
* Reinforcement Learning from Human Feedback (RLHF)

<figure><img src="../../.gitbook/assets/image (311).png" alt=""><figcaption></figcaption></figure>

## ChatGPT

Code Generation

## BART（encoder-decoder）

<figure><img src="../../.gitbook/assets/image (312).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (313).png" alt=""><figcaption></figcaption></figure>

预训练任务是一个<mark style="color:red;">去噪声的任务</mark>（Denoising Task）：

* Token Masking
* Token Deletion
* Sentence Permutation（句子顺序调换）
* Document Rotation
* Text infilling（不定长增加）

## T5（encoder-decoder）

<figure><img src="../../.gitbook/assets/image (314).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (315).png" alt=""><figcaption></figcaption></figure>
