# Informed (heuristic) Search

## Why informed (heristic) search?

AI problem solver employs heuristics in two situations:

1. A problem may not have an exact solution because of ambiguities in problem statement or available data （例如医疗诊断）
2. A problem may have an exact solution, but the computational cost (time and space) of finding it may be prohibitive.&#x20;

## Informed vs Uninformed Search

* Uninformed searches are normally very inefficient
* Information about the problem can sometimes be used to guild the search more efficiently
* Informed search explores the node that is most "likely" to be the nearest to a goal state
* Informed search works successfully in many cases, but its success is not guaranteed 不保证成功

## Heuristic Search Methods

Methods that use a heuristic function to provide specific knowledge for the problem:

[hill-climbing.md](hill-climbing.md "mention") [greedy-search-best-first-search.md](greedy-search-best-first-search.md "mention") [a-algorithm.md](a-algorithm.md "mention")
