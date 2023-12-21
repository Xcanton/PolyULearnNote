# Heap Structure

本节主要讨论最大堆（Max Heap）。

## What is Heap?

* A data structure that supports fast retrieval of the maximum value
* Also called a priority queue, used for managing a set of items based on their "priority"

在一个堆中，只要满足当前分叉中，两个子节点都比主节点小即可。

$$
A[Parent(i)] \geq A[i]
$$

对于一个确定的堆，从它任意一个节点i我们可以知道：

$$
Parent(i)=\lfloor(i-1)/2\rfloor
$$

$$
Left(i)=2i+1
$$

$$
Right(i)=2i+2
$$

对于整一个堆的树状结构而言，高度也是确定的：

$$
height=\lfloor\log_2n\rfloor
$$

## Instance Variables

<figure><img src="../../.gitbook/assets/image (111).png" alt=""><figcaption><p>Variables of Heap</p></figcaption></figure>

## Operations

<figure><img src="../../.gitbook/assets/image (112).png" alt=""><figcaption><p>Operations of Heap</p></figcaption></figure>

### Max-Heapify

<figure><img src="../../.gitbook/assets/image (113).png" alt=""><figcaption><p>pseudocode for Max-Heapify</p></figcaption></figure>

* 从本身节点找到最大的，放到主节点上，并向上回溯或向下回溯。

### Build-Max-Heap

<figure><img src="../../.gitbook/assets/image (114).png" alt=""><figcaption><p>pseudocode for Build Max Heap function</p></figcaption></figure>

* 不需要管所有的叶子节点，只需要从一半-1的位置开始即可，比较时会带上叶子节点考虑。

### Get-Max

<figure><img src="../../.gitbook/assets/image (116).png" alt=""><figcaption><p>pseudocode for Get Max from Heap</p></figcaption></figure>

### Extract-Max

<figure><img src="../../.gitbook/assets/image (117).png" alt=""><figcaption><p>pseudocode for Extract-Max from Heap</p></figcaption></figure>

* 先弹出堆顶元素
* 然后将堆尾元素放到堆顶
* 最后从堆顶重新构建堆

### Update-Key

<figure><img src="../../.gitbook/assets/image (118).png" alt=""><figcaption><p>pseudocode for Update Key in Heap</p></figcaption></figure>

* 如果更新的key更小了，那就向下维护堆
* 如果更新的key更大的，那就向上维护堆

### Insert-Key

<figure><img src="../../.gitbook/assets/image (119).png" alt=""><figcaption><p>pseudocode for Insert Key in Heap</p></figcaption></figure>

* 将堆尾置为无穷小
* 更新堆尾元素，这样就能一直向上循环维护堆结构了

## HeapSort

<figure><img src="../../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

* 先构建一个最大堆，然后将最大的依次放到最后
