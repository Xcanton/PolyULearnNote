# File Organization

## 数据库的本质

* Store a database as a collection of files
* Store a file as sequences of records
* A record is a sequence of fields

通过多个文件存储的记录，每个文件中包含一系列的数据row，并且每个row具有相同的组织形式schema

## File Structure

### Simple Approach

通过一个文件来存数据库中的一个表（a file is used to store a relation）， 那么可以通过schema预测这个文件的绝对大小（Assume fixed record size）。

Store record i at byte n\*(i-1), n is the size of a record

#### 弊端

每一条记录的长度不能超过处理器读取block的大小

#### 如何删除数据

* 删除一条数据，并将后续的数据向前移动
* 删除一条数据，将最后一条数据移动到当前数据的位置
* 两种方法都需要额外的内存开销

### Free Lists

本质上还是文件，但是额外存储一个链表，用于标记文件中空的row。

<figure><img src="../../../.gitbook/assets/image (21).png" alt=""><figcaption><p>Free List Organization via Empty record List</p></figcaption></figure>

#### 好处

* 在删除中，不需要额外操作文件
* 在插入中，可以重复利用同一空间

#### 如何插入数据

* 通过链表找到第一个空的record row，修改链表并插入数据

### Sequential File Organization

为了保证主键的顺序性，上述方法还需在增删改查的时候维护整体数据主键的顺序，有额外开销

所以提出通过链表作为额外的顺序判断依据，不以文件中实际顺序。

<figure><img src="../../../.gitbook/assets/image (20).png" alt=""><figcaption><p>Sequential File Organization via Linked List</p></figcaption></figure>

#### 好处

* 适合需要对整个文件进行操作的应用（查询工资大于一万的人）
* 整个文件可以通过额外的链表表示（去除空数据）（The records in the file are ordered by a search-key）
* 可以跨文件保存数据

#### 如何删除数据

* use pointer chains
* 可以与Free List结合，额外存储空链表的方式进行存储

#### 如何插入数据

* 如果空链表中有位置，即插入该位置
* 如果数据块中有位置，空链表为空，则插入该数据块中，并更新链表
* 如果没有空位置，将数据插入一个新的block（overflow block），并且在链表中找到正确位置，插入数据指针（pointer chain must be updated）

## Index Structure

本质上，上述的方式都是文件，并没有对key做出优化，这样对某些查询的时候，需要排序或者全遍历，存在优化空间。

* Search Key： Attribute to sets of attributes used to look up records in a file
* Index File: an index file consists of records (index entries) of the form {search-key, pointer}![](<../../../.gitbook/assets/image (22).png>)

Index的数据类型：

* Ordered Index： search keys are stored in sorted order
  * 通常是Tree-based
  * 支持范围查询和等于查询
* Hash Index： search are distributed uniformly across "buckets" using a "hash function"
  * 只能快速相应等于的情况，不支持范围查询

### Ordered Index

在顺序索引中，索引实例被保存在按顺序存储的键值对中。

#### Primary Index（clustering index）

索引的数量与数据记录（record）数量一致。多被用在primary key上。

#### Secondary index（non-clustering index）

索引数量少于实际数据数量（an index whose search key specifies an order different from the sequential order of the file）

<figure><img src="../../../.gitbook/assets/image (23).png" alt=""><figcaption><p>Primary Index and Secondary Index</p></figcaption></figure>

#### Dense Index

当前search key的所有可能值都包含在当前index中。

<figure><img src="../../../.gitbook/assets/image (24).png" alt=""><figcaption><p>Dense Index</p></figcaption></figure>

#### Sparse Index

当前search key不完全包含在当前index中，要求原始数据按照顺序保存或按照顺序读取。

* 能够节省存储空间
* 但是增加了查询的开销
* 可以用sparse index记录不同数据块的头地址

<figure><img src="../../../.gitbook/assets/image (25).png" alt=""><figcaption><p>Sparse Index</p></figcaption></figure>

<mark style="color:red;">Secondary Index必须是Dense的</mark>，因为没有办法保证数据内部的顺序。

