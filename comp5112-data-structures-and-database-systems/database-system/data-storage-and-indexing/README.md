# Data Storage & Indexing

## [#li-ti](b+-tree-organization.md#li-ti "mention")-如何计算B+树的n和查询时间

{% content-ref url="b+-tree-organization.md" %}
[b+-tree-organization.md](b+-tree-organization.md)
{% endcontent-ref %}

<figure><img src="../../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

## 如何选择Index

如果考虑平均时间复杂度，并且有一个比较好的hash函数，可以用hash index；如果考虑最坏时间复杂度，可以用B+树
