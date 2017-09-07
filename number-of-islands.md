# Number of Islands

## Project Description

Given a 2d grid map of`'1'`s \(land\) and`'0'`s \(water\), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

**Example 1:**

```
11110
11010
11000
00000
```

Answer: 1

**Example 2:**

```
11000
11000
00100
00011
```

Answer: 3

> Companies: Amazon, Microsoft, Google, Facebook, Zenefits

## Analysis

This problem can be solved with DFS/BFS. Iterate through grid, when found a 1, do dfs to make all connected 1s to be 0.

"Need to change str to list in grid first"

## Solution

D**FS**

```py
class Solution(object):
    def numIslands(self, grid):
        """
        :type grid: List[List[str]]
        :rtype: int
        """
        self.m = len(grid)
        self.n = len(grid[0]) if self.m != 0 else 0
        if self.m == 0 or self.n == 0:
            return 0
        for i in range(self.m):
            grid[i] = list(grid[i])
        nums = 0
        for i in range(self.m):
            for j in range(self.n):
                if grid[i][j] == '0':
                    continue
                else:
                    nums += 1
                    self.dfs(grid, i, j)
        return nums
    def dfs(self, grid, i, j):
        if i < 0 or i >= self.m or j < 0 or j >= self.n:
            return
        if grid[i][j] == "1":
            grid[i][j] = "0"
            self.dfs(grid, i, j+1)
            self.dfs(grid, i, j-1)
            self.dfs(grid, i+1, j)
            self.dfs(grid, i-1, j)
            
```

**BFS**

```py
class Solution(object):
    def numIslands(self, grid):
        """
        :type grid: List[List[str]]
        :rtype: int
        """
        self.m = len(grid)
        self.n = len(grid[0]) if self.m != 0 else 0
        if self.m == 0 or self.n == 0:
            return 0
        for i in range(self.m):
            grid[i] = list(grid[i])
        nums = 0
        for i in range(self.m):
            for j in range(self.n):
                if grid[i][j] == '1':
                    nums += 1
                    self.bfs(grid, i, j)
        return nums
    
    def bfs(self, grid, x, y):
        grid[x][y] = "0"
        queue = [(x, y)]
        while len(queue) != 0:
            i, j = queue.pop(0)
            if i > 0 and grid[i-1][j] == '1':
                queue.append((i-1, j))
                grid[i-1][j] = '0'
            if i < self.m - 1 and grid[i+1][j] == '1':
                queue.append((i+1, j))
                grid[i+1][j] = '0'
            if j > 0 and grid[i][j-1] == '1':
                queue.append((i, j-1))
                grid[i][j-1] = '0'
            if j < self.n - 1 and grid[i][j+1] == '1':
                queue.append((i, j+1))
                grid[i][j+1] = '0'
```



