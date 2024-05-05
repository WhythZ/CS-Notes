[Week 0 Search - CS50's Introduction to Artificial Intelligence with Python (harvard.edu)](https://cs50.harvard.edu/ai/2024/weeks/0/)
# Search Algorithm
## DFS（Depth-First Search 深度优先算法）
- search algorithm that always expands the deepest node in the frontier
- 使用stack数据结构（last-in first-out data type）进行node的拓展过程中的节点记录，即最后被放入结构的节点是最先被删除的，即最后被放入的节点是最先要被探索完的，即深度优先
## BFS（Breadth-First Search 广度优先算法）
- search algorithm that always expands the shallowest node in the frontier
- 使用queue数据结构（first-in first-out data type）