# How to Process Selection Operation

在Evaluation Machine中，对查询操作有不同的方式，各种方式对时间复杂度不同，但是对数据也具有一定的要求（[索引结构](../data-storage-and-indexing/)）。

<figure><img src="../../../.gitbook/assets/image (101).png" alt=""><figcaption><p>Selection Operation Cost in different Algorithms</p></figcaption></figure>

* br：在这个查询的表中有多少个block
* hr：B+树的高度（也等于B+树的搜索cost）+1
* b\_result：结果预计占多少个block
* n\_result：结果预计有多少行（Secondary Index非连续，所以需要全部获取）

## Linear Search (线性搜索，遍历)

该方式就是遍历所有的数据，对数据结构没有要求，但是时间较慢。

$$
Cost=b_r\ blocks
$$



## Primary Index on Candidate Key, Equality (查询主键有对等的Index)

该方法是通过候选建上的Index结构，对==查询进行优化。由于树结构对查询复杂度是树的高度，那么多出来的1是对输出的衡量（返回结果的地址，由于候选键是连续的，所以只需要返回头节点）。

$$
Cost=h_r+1\ blocks
$$

$$
B+\ Tree\ height\ h_r=\lceil \log_{\lceil f/2 \rceil}{n_r}\rceil
$$

* n\_r：在表中的记录数量
* f：B+树节点中，有多少个children

## Primary Index on Non-Key, Equality（非主键的对等Index）

该方式还是通过查询的键上的Index结构进行查询，但是由于是非主键，所以block之间没有顺序关系，所以需要返回所有的block头节点。

$$
Cost=h_r+b_{match}\ blocks
$$

* b\_match：预估出来的，结果需要多少个blocks（需要好的预估算法和精确的历史）

## Secondary Index on NonKey, Equality（非主键的不对等Index）

该方式与上述方式相似，对非主键的非对的Index进行搜索，所以需要返回所有的数据（由于Index的不对等性，不能保证知道对应键就能搜索到所有值域）

$$
Cost=h_r+n_{match}\ blocks
$$

* n\_match：预估出来的，结果需要多少行（也需要好的预估算法和精确的历史）

## Range Search （范围搜索 eg. 工资大于一万）

如果是B+ Tree结构，按照equality找到分隔点，按照Index特性进行输出。
