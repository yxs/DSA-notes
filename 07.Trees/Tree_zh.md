# 树

常考的是二叉树、二叉搜索树的各种操作，深搜、广搜

## 概念

树就是一种特殊的图

确认二叉树的根节点深度定义成 1 还是 0？

## 模版 & 基本操作

### 相同的树 & 树的深度/宽度/直径 & 树的翻转/合并/路径和 & 节点的公共祖先

### 树的序列化和反序列化

### 前序遍历 & 中序遍历 & 后序遍历 & 层次遍历


中序遍历，左-中-右

94. Binary Tree Inorder Traversal

```python

```




Ref. [图解 二叉树的四种遍历](https://leetcode-cn.com/problems/binary-tree-preorder-traversal/solution/tu-jie-er-cha-shu-de-si-chong-bian-li-by-z1m/)

### 深度优先搜索 & 广度优先搜索

#### DFS

当回溯用于树的时候，就是深度优先搜索。区别在于回溯更关注状态，前进设置状态，回退撤销状态，而 DFS 关注查找某个条件。


bfs框架

```java
// 计算从起点 start 到终点 target 的最近距离
int BFS(Node start, Node target) {
    Queue<Node> q; // 核心数据结构
    Set<Node> visited; // 避免走回头路

    q.offer(start); // 将起点加入队列
    visited.add(start);
    int step = 0; // 记录扩散的步数

    while (q not empty) {
        int sz = q.size();
        /* 将当前队列中的所有节点向四周扩散 */
        for (int i = 0; i < sz; i++) {
            Node cur = q.poll();
            /* 划重点：这里判断是否到达终点 */
            if (cur is target)
                return step;
            /* 将 cur 的相邻节点加入队列 */
            for (Node x : cur.adj())
                if (x not in visited) {
                    q.offer(x);
                    visited.add(x);
                }
        }
        /* 划重点：更新步数在这里 */
        step++;
    }
}
```

## 参考