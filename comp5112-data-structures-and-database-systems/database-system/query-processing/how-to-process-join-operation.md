# How to Process Join Operation

与Selection相似，但是需要考虑两个表，并根据连接条件判断是否连接。在关系代数表达式中表示为：![](<../../../.gitbook/assets/image (182).png>)

<figure><img src="../../../.gitbook/assets/image (183).png" alt=""><figcaption></figcaption></figure>

## Nested-Loop Join

该方式就是嵌套两层循环，找出所有匹配的数据。爆慢，应该是最慢的方式。

<figure><img src="../../../.gitbook/assets/image (174).png" alt=""><figcaption><p>pseudocode of Nested-Loop Join</p></figcaption></figure>

由于读入的时候，表r在外层，所以只用读入b\_r的block数量，但是由于表s在内层循环，所以需要读入表r记录数倍的block数量。

$$
Cost = n_r \times b_s + b_r\ blocks
$$

* n\_r：表r的数据条数
* b\_s：表s的block数
* b\_r：表r的block数

## Index Nested-Loop Join

该方式与上述方式相似，就是内层循环的查找换成有特定Index结构的查找，即将b\_s替换成更小的查找复杂度。

但是该方式需要内层循环的数据具有一定的索引结构。

<figure><img src="../../../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption><p>pseudocode of Index Nested-Loop Join</p></figcaption></figure>

内层循环的复杂度为h\_s+1，由于输出块地址所以+1，h\_s为树的高度（如果是B+ Tree）。这个例子是[主键索引](how-to-process-selection-operation.md#primary-index-on-candidate-key-equality-cha-xun-zhu-jian-you-dui-deng-de-index)，其他方式需要将整体替换成[其他的时间复杂度](how-to-process-selection-operation.md)。

$$
Cost = n_r \times (h_s + 1)+ b_r\ blocks
$$

* h\_s + 1：是B+ Tree的primary key search的时间复杂度。

### <mark style="color:red;">例题</mark>

<figure><img src="../../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption><p>Exercise on how to compute the cost of nested-loop join</p></figcaption></figure>

* 对两个table在外层循环的情况分别讨论，并带入![](<../../../.gitbook/assets/image (7) (1).png>)计算
* 如果内层循环有index，那么计算器复杂度。
* 如果内层循环是B+ Tree，那么用B+ Tree的搜索复杂度![](<../../../.gitbook/assets/image (8) (1).png>)+1计算，结合了B+ Tree的[树高计算](../data-storage-and-indexing/b+-tree-organization.md#li-ti)和[对称主键搜索](how-to-process-selection-operation.md#primary-index-on-candidate-key-equality-cha-xun-zhu-jian-you-dui-deng-de-index)。

## Block Nested-Loop Join

<figure><img src="../../../.gitbook/assets/image (9) (1).png" alt=""><figcaption><p>pseudocode of Block Nested-Loop Join</p></figcaption></figure>

这个方式是对外层循环的表组织进行优化，通过对外层循环对应的表的blocks数量进行优化，不再循环所有的行数，只循环blocks数量。

$$
Cost = \lceil b_r / (M-2) \rceil \times b_s + b_r \  blocks
$$

* M：系统中能够读取最多多少个blocks，由于需要保留一个block用于内层循环，和一个clock用作输出，所以-2。
* 所以向上取整，能够得到外层循环的次数。

## Merge Join

该方式是希望通过对表r和表s先进行排序，由于排序后所有的数值都是按照顺序，那么可以类似双指针的方式快速查找。所以这一步的时间复杂度为：

$$
Cost= b_r + b_s \  blocks + \ the \ sorting \ cost \ (if \ unsorted)
$$

### Sorting: External Sort-Merge

这部分关注如何在内存blocks中进行sorting，方法类似于sort-merge algorithm，先分治后合并。那么对于排序的时间复杂度为：

$$
Sorting Cost = b_r(2 \lceil\log_{M-1}{(b_r / M) } \rceil + 1)
$$

* 外面b\_r对应的是合并时排序的开销，是线性开销
* 内层由于M需要保留一个作为结果输出，所以log取M-1，但是对分治的时候，可以同时进行M个，所以向上取整。
* 由于读取和传输数据，所以需要乘以2，然后加上一个输出用的block

所以总体的开销为：

$$
Cost= b_r + b_s + \\ b_r(2 \lceil\log_{M-1}{(b_r / M) } \rceil + 1) + \\ b_s(2 \lceil\log_{M-1}{(b_s / M) } \rceil + 1)  \  blocks
$$

## Hash Join

通过Hash函数对两个表进行哈希并且分桶，后续的match只在同一个桶中进行分隔。

1. 根据内存能够处理多少个blocks，计算partitions数量（表数量 / M-2）向上取整。
2. 判断合并时能不能一次合并完（one pass），即1的结果是不是小于等于M。
3. 如果2满足，那么总消耗如下：

$$
Cost = 3(b_r + b_s)
$$

### <mark style="color:red;">例题</mark>

<figure><img src="../../../.gitbook/assets/image (10) (1).png" alt=""><figcaption><p>Exercise of Computing Partition Num and Total Cost of Hash Join</p></figcaption></figure>
