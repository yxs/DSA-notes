# 数组

## 概念


### hash冲突 Hash collisions

开放地址，再哈希，链地址，建立公共溢出区

hashing collision chaining vs open addressing

jdk1.8 用的拉链（chaining）

拉链更简单，平均查找长度较短。适合于造表前无法确定表长。开放定址法为减少冲突，要求装填因子α较小，而拉链不用，省空间。
删除结点的操作易于实现。

开放地址适用于小规模，cache友好。


https://zhuanlan.zhihu.com/p/29520044

https://stackoverflow.com/a/2557451/8202659

### Matrix 二维数组

## 模版 & 基本操作

### hash

检查重复值，`set()` 遍历即可

找出不同值，需要计数的时候，用 python3 `Counter()` 很方便，有时候则需要通过计算 Ascii Table 的相对位置来作为 key，比如某个字母相对小写字母 `a` 的位置 `ord[c] - ord("a")`

当遍历 list 同时需要 k, v 时，可以 `for i, num in enumerate(nums)`

### 深度优先搜索 & 广度优先搜索 in Matrix

对比 DFS 和 BFS：比如 leetcode 1293 有障碍物的二维网格中寻找最短路径，BFS 逐层向外扩展的搜索可以更早的遇见障碍，提前返回。

DFS 需要记忆化来优化时间复杂度

BFS类似波纹

以 [200. Number of Islands](https://leetcode-cn.com/problems/number-of-islands/) 为例

DFS 用递归实现

```python
def dfs(self, grid, r, c):
    grid[r][c] = 0
    nr, nc = len(grid), len(grid[0])
    for x, y in [(r - 1, c), (r + 1, c), (r, c - 1), (r, c + 1)]:
        if 0 <= x < nr and 0 <= y < nc and grid[x][y] == "1": # 满足某些条件
            self.dfs(grid, x, y)
```

BFS 用队列实现，先进先出

```python
neighbors = collections.deque([(r, c)])
while neighbors:
    row, col = neighbors.popleft()
    for x, y in [
        (row - 1, col),
        (row + 1, col),
        (row, col - 1),
        (row, col + 1),
    ]:
        if 0 <= x < nr and 0 <= y < nc and grid[x][y] == "1":
            neighbors.append((x, y))
            grid[x][y] = "0"
```


## 参考