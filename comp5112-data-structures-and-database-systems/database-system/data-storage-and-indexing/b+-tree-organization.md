# B+ Tree Organization

## B+Tree Structure

上述的Index方式需要额外维护不同Index的更新，并且需要读入整个Index文件或者block，实际中不高效。希望树结构中包含更多数据的信息。

B+树本质上是 n不为2的二叉树，并且n可以通过计算单元的block大小和存储的数据类型计算得出，是的每一个block在处理的时候尽可能多的读入信息。

B+树的顺序只在leaf node上记录，中间的节点是用作排序的。

<figure><img src="../../../.gitbook/assets/image (26).png" alt=""><figcaption><p>B+Tree Index on Names</p></figcaption></figure>

### B+ Tree Node Structure

<figure><img src="../../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

* K is a search-key value
* P is a pointer to a child node(for non-leaf node) or a pointer to a record(for leaf node)
* 所有在Pi指针指向的子树SK中的search-key需要满足以下条件：

$$
K_{i-1} \leq {SK}_{?} 	\leq K_i
$$

* 所有在同一节点中的search-key需要满足以下条件：

$$
K_{1} \leq K_{2} \leq K_{3} \leq ... \leq K_i
$$

* 叶节点（leaf node）需要存储 <mark style="color:red;">\[(n-1)/2]</mark> 到 <mark style="color:red;">n-1</mark> 个值（最后一个pointer被用来指向下一个节点的头的数据了）。
* 枝干节点（each node that is not a root or a leaf）需要存储 <mark style="color:red;">\[n/2]</mark> 到 <mark style="color:red;">n</mark> 个值。

### B+Tree的特性

树的高度是固定的：

$$
height = \lceil \log_{\lceil n/2 \rceil}{NK} \rceil
$$

那么查询一条记录的开销也是固定的：

$$
cost = \lceil \log_{\lceil n/2 \rceil}{NK} \rceil
$$

#### <mark style="color:red;">例题</mark>

<figure><img src="../../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

* 对于读进一个block的数据而言，即是一个Node而言，有n个指针和n-1个search-key，所以可以得出总大小
* 总大小必须小于等于block的大小，所以向下取整可以得到一个node的数据数量
* 那么查找的开销就可以通过公式计算得出，即B+树的节点n数量的一半的log，对所有search-key取这个log值。也可以通过下面方法算出：

$$
\log_{50}{1\_million} = \log{1\_million} / log{50}
$$

### B+ Tree Query

<figure><img src="../../../.gitbook/assets/image (29).png" alt=""><figcaption><p>Pseudocode for Query in B+ Tree</p></figcaption></figure>

### B+ Tree Insertion

1. 通过搜索，确定search-key是否存在需要插入的值，如果没有即找到了插入位置
2. 如果找到了对应的值：
   1. 在文件中加入一条record
   2. 如果需要的话，更新桶节点的Linked List
3. 如果没有找到对应的值
   1. 在文件中添加一条对应的值，并创建一个新的桶？（and create a bucket if necessary）
   2. 如果叶子结点仍有空余，那么插入对应的(key-value, pointer)键值对
   3. 如果叶子结点没有空余，那么尽兴节点分隔，并向上更新节点。

<figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption><p>B+ Tree before and after insertion of Adams</p></figcaption></figure>

1. Splitting a leaf node
   1. 按键值对顺序将新的节点插入，并将前n/2个作为原始的节点，将后续的构成一个新的节点
   2. 如果新节点是p，k是p的最小的值，那么将（k，p）插入到父节点中
2. 更新父节点，直至遇到仍有空余位置的节点（non-full node）

### B+ Tree Deletion

与[B+ Tree Insertion](b+-tree-organization.md#b+-tree-insertion)是相反的，不同的是：需要判断节点是否大于50% full，如果不是判断如何跟前面的节点合并或重新分配。这个合并和重新分配节点的过程也是向上回溯的。

## B+ Tree File Organization

可以通过B+ Tree直接存储某些Attribute。

好处是，可以在查询的过程中，直接获取对应的数值。

坏处是，对节点的复杂度有损坏，即每个node包含的信息量小了。

<figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption><p>Examples of B+ Tree Organization on Attributes</p></figcaption></figure>
