# Linked List（链表）

## Node Class

<figure><img src="../../../.gitbook/assets/image (155).png" alt=""><figcaption><p>pseudocode for Node in Linked List</p></figcaption></figure>

节点（Node）是链表最基本的单元，对\[doubly] linked list，每个节点包括以下三个部分：

* key：节点所保存的数据（key value of the node）
* prev：上一节点（pointer to the previous node）
* next：下一节点（pointer to the next node）
* 指针可以被设置成nullptr或者其他node

## \[Doubly] Linked List

<figure><img src="../../../.gitbook/assets/image (156).png" alt=""><figcaption><p>pseudocode for Linked List Class</p></figcaption></figure>

链表就是一串相互连接的节点组成的数据结构，需要满足以下条件：

* head is the first node in the linked list
* 第一个节点的prev=nullptr， 最后一个节点的next=nullptr
* 连续的两个节点x和y必须满足：

$$
x.next=y\ and \ y.prev=x
$$

### Operations

#### search(k)

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>pseudocode for LinkedList.search(k)</p></figcaption></figure>

* Search a node with a key value k

#### insert(x)

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>pseudocode for LinkedList.insert(x)</p></figcaption></figure>

* insert a node into a linked list
* 如果原链表不是空链表，那么需要将头节点的prev指针指向新节点

#### remove(x)

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>pseudocode for LinkedList.remove(x)</p></figcaption></figure>

* remove an (existing) item from a linked list
* 如果是头节点，只需要把x.next放到head
* 如果x.next不为空，也要调整下一节点的prev指针
