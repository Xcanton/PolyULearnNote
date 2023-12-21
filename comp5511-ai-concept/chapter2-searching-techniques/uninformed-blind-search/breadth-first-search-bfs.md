# Breadth-first Search (BFS)

需要一个Open List 来存放候选节点（that have been generated but their children have not been examined）和一个Close List 来存放所有访问过的节点（visited）。

<figure><img src="../../../.gitbook/assets/image (144).png" alt=""><figcaption><p>Example of BFS</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (145).png" alt=""><figcaption><p>pseudocode of BFS</p></figcaption></figure>

当获取节点时才判断是否是目标状态，如果是即刻返回，不更新节点。

## Completeness

Complete，总能找到最优解

## Time Complexity

$$
O(b^{m+1})
$$

* m是解的高度（节点层数-1）

## Space Complexity

$$
O(b^{m+1})
$$

* m是解的高度（节点层数-1）

由于需要把上层全搜完
