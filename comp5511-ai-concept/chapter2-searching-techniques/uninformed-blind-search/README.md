# Uninformed (Blind) Search

只能区分当前是不是目标状态（The only information available is the ability to distinguish goal state from non-goal state）。

An uninformed(blind) search algorithm uses no information other than the initial state, the search operator and a test foro a solution.

The different types of blind searches are characterized by the order in which they expand the nodes. This can have a dramatic effect on how well the search performs.

## Evaluation Criteria

* Completeness
* Speed
* Memory
* Measured in terms of&#x20;
  * d = depth of the search tree
  * b = (average) branching factor of the tree
  * m = depth of the shallowest solution

## Methods

[breadth-first-search-bfs.md](breadth-first-search-bfs.md "mention") [depth-first-search-dfs.md](depth-first-search-dfs.md "mention")

### DFS vs BFS

* DFS与深度直接相关，如果最大深度比解的深度大很多的话，那么就可能浪费很多时间。当然也与随机有关，如果先遇到解的分支，那可能会比后遇到快很多。
* BFS需要非常大的内存。

