## Array

## Matrix

- 4 Directions

- 8 Directions

### Depth First Search & Breadth First Search in Matrix

DFS vs BFS:

For example, [1293. Shortest Path in a Grid with Obstacles Elimination](https://leetcode.com/problems/shortest-path-in-a-grid-with-obstacles-elimination/)

BFS is like ripples. The advantage of BFS is that searches that scale out layer by layer can encounter obstacles earlier and return early. However, DFS requires memory to optimize time complexity.

[200. Number of Islands](https://leetcode.com/problems/number-of-islands/)

DFS is implemented recursively

```python
def dfs(self, grid, r, c):
    grid[r][c] = 0
    nr, nc = len(grid), len(grid[0])
    for x, y in [(r - 1, c), (r + 1, c), (r, c - 1), (r, c + 1)]:
        if 0 <= x < nr and 0 <= y < nc and grid[x][y] == "1": # Some conditions are met
            self.dfs(grid, x, y)
```

BFS is implemented with a queue, first in first out

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

## Ref.

https://www.geeksforgeeks.org/difference-between-bfs-and-dfs/