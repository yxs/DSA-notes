# 图

## 概念

## 模版 & 基本操作


### 深度优先搜索 & 广度优先搜索 & 并查集 & 拓扑排序

对比 DFS 和 BFS：

比如 leetcode 1293 有障碍物的二维网格中寻找最短路径，BFS 逐层向外扩展的搜索可以更早的遇见障碍，提前返回。

#### Union Find 并查集


```python
class UnionFind:
    def __init__(self):
        """
        记录每个节点的父节点
        """
        self.father = {}

    def find(self, x):
        """
        查找根节点
        路径压缩
        """
        root = x

        while self.father[root] != None:
            root = self.father[root]

        # 路径压缩
        while x != root:
            original_father = self.father[x]
            self.father[x] = root
            x = original_father

        return root

    def merge(self, x, y, val):
        """
        合并两个节点
        """
        root_x, root_y = self.find(x), self.find(y)

        if root_x != root_y:
            self.father[root_x] = root_y

    def is_connected(self, x, y):
        """
        判断两节点是否相连
        """
        return self.find(x) == self.find(y)

    def add(self, x):
        """
        添加新节点
        """
        if x not in self.father:
            self.father[x] = None

```

#### 拓扑排序

拓扑排序有两种实现方式，时间复杂度均为 $O(V+E)$，分别是

**入度表**：维护一个入度为 0 的顶点的集合
  
1. 从 DAG (directed acyclic graph) 图中选择一个没有前驱（即入度为 0）的顶点并输出
2. 从图中删除该顶点和所有以它为起点的有向边
3. 重复 1, 2 直到当前的 DAG 图为空或当前图中不存在无前驱的顶点为止，后一种情况说明有向图中必然存在环

> 算法可视化 https://www.cs.usfca.edu/~galles/visualization/TopoSortIndegree.html


**DFS** 深度优先搜索

## 参考