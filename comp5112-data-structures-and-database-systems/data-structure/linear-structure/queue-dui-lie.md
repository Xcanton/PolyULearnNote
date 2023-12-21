---
description: Queue
---

# Queue（队列）

The First-in First-out (FIFO) property，通常用数组实现。

## Instance Variables

* Q：用于存放数据的数组（an array of items）
* length：数组最大长度（length of array Q）
* f：队列头元素的位置（the front position）
* sz：队列中元素的个数（the number of items stored）

对于当前位置，可以通过头节点位置和队列长度计算得出：

$$
r=(f+sz)\ mod\ length
$$

## Operations

### enqueue(e)

<figure><img src="../../../.gitbook/assets/image (134).png" alt=""><figcaption><p>pseudocode for Queue.enqueue(e)</p></figcaption></figure>

* insert item e (at the rear of the queue)
* 需要判断队列是否满了

### dequeue()

<figure><img src="../../../.gitbook/assets/image (135).png" alt=""><figcaption><p>psedocode for Queue.dequeue()</p></figcaption></figure>

* extract the item from the front
* 需要判断队列是否为空

### size()

<figure><img src="../../../.gitbook/assets/image (225).png" alt=""><figcaption><p>pseudocode for Queue.size()</p></figcaption></figure>

* return the number of items stored

### isEmpty()

<figure><img src="../../../.gitbook/assets/image (226).png" alt=""><figcaption><p>pseudocode for Queue.isEmpty()</p></figcaption></figure>

* check whether the queue is empty

### front()

<figure><img src="../../../.gitbook/assets/image (227).png" alt=""><figcaption><p>pseudocode for Queue.front()</p></figcaption></figure>

* return the front item without removing it
* 仅查看，不弹出元素
* 需要判断队列是否为空
