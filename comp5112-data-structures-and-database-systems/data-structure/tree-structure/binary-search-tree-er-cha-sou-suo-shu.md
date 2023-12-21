# Binary Search Tree（二叉搜索树）

为了高效的搜索、插入和删除而给二叉树添加既定的规则，要求左子节点的值都小于自身节点，自身节点还小于所有右子节点的值。

## Operations

<figure><img src="../../../.gitbook/assets/image (129).png" alt=""><figcaption><p>Binary Search Tree's Operations</p></figcaption></figure>

* h：是树的高度，但是可能退化成O(n)

### Search

<figure><img src="../../../.gitbook/assets/image (130).png" alt=""><figcaption><p>pseudocode for Search</p></figcaption></figure>

### Minimum

<figure><img src="../../../.gitbook/assets/image (131).png" alt=""><figcaption><p>pseudocode for Minimum</p></figcaption></figure>

### Insertion

<figure><img src="../../../.gitbook/assets/image (132).png" alt=""><figcaption><p>pseudocode for Insertion</p></figcaption></figure>

* 首先先找到一个合适的插入位置，然后再插入节点。
* 若没有找到节点，即找到空节点，那么意味着树为空，插入至root。

### Deletion

<figure><img src="../../../.gitbook/assets/image (133).png" alt=""><figcaption><p>pseudocode for Deletion</p></figcaption></figure>

* 如果删除的没有左子节点或者右子节点，那么将右或左子节点连接到删除节点的位置
* 如果两个都有，那么从左子树找到最小的节点，删除改节点，并且将改节点替换成本次要删除的节点
