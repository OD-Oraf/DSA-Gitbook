# DFS vs BFS

When is it preferential to use either algorithm

* DFS
  * DFS is preferred  when the goal is to visit every node in the graph, especially when the graph is deep.
  * DFS is also more memory-efficient than BFS for deep graphs since it doesn't need to store nodes at each level(better space efficiency)
* BFS
  * Generally better at finding shortest path or the minimum number of steps to reach a target node&#x20;
    * Searches all neighbor nodes before moving onto the next level
  * If solution is not far from root then BFS may likely be faster as it is more optimal for a tree that is wide than deep
  * Not good for wide trees since it needs to store all the variables at a level in memory
