# Day-11

---

## 1. Number of Islands using BFS

```python
from collections import deque

m, n = map(int, input().split())
grid = [list(map(int, input().split())) for _ in range(m)]

k = 0
d = [(-1, 0), (1, 0), (0, -1), (0, 1)]

for i in range(m):
    for j in range(n):
        if grid[i][j] == 1:
            k += 1
            grid[i][j] = 0
            q = deque()
            q.append((i, j))
            while q:
                r, c = q.popleft()
                for dr, dc in d:
                    nr, nc = r + dr, c + dc
                    if 0 <= nr < m and 0 <= nc < n and grid[nr][nc] == 1:
                        grid[nr][nc] = 0
                        q.append((nr, nc))

print(k)
```

**Input:**
```
4 5
1 0 1 0 0
1 1 0 1 1
0 0 1 0 0
1 0 1 1 1
```

**Output:**
```
5
```

---

## 2. Max Length of a Substring with At Most K Distinct Characters

```python
s = input()
k = int(input())

d = {}
i, j = 0, 1
m = 1

while j < len(s):
    if len(d) > k:
        a = list(d)[0]
        i = d[a] + 1
        m = max(m, j - i)
        d.pop(a)
    else:
        if s[j] in d:
            d[s[j]] = j
            j += 1 
        else:
            d[s[j]] = j 
            j += 1
        m = max(m, j - i - 1)

print(m)
```

**Input:**
```
abaaedacdefaaa
3
```

**Output:**
```
5
```

---

## 3. Max Area of Island (Leetcode #695)

```python
class Solution:
    def maxAreaOfIsland(self, grid: List[List[int]]) -> int:
        def isl(i, j):
            if i == m or j == n or i == -1 or j == -1 or grid[i][j] != 1:
                return 0

            grid[i][j] = 3
            return 1 + isl(i + 1, j) + isl(i, j + 1) + isl(i, j - 1) + isl(i - 1, j)

        m, n = len(grid), len(grid[0])
        k = 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == 1:
                    k = max(k, isl(i, j))
        return k
```

---

## 4. Perimeter of Island (Leetcode #463)

```python
class Solution:
    def islandPerimeter(self, grid: List[List[int]]) -> int:
        def island(i, j):
            if i == m or j == n or i == -1 or j == -1 or grid[i][j] == 0:
                return 1
            if grid[i][j] == 2:
                return 0
            grid[i][j] = 2
            return island(i, j + 1) + island(i, j - 1) + island(i - 1, j) + island(i + 1, j)

        m, n = len(grid), len(grid[0])
        for i in range(m):
            for j in range(n):
                if grid[i][j] == 1:
                    return island(i, j)
        return 0
```

**Input:**
```python
grid = [[0,1,0,0],
        [1,1,1,0],
        [0,1,0,0],
        [1,1,0,0]]
```

**Output:**
```
16
```

---

## 5. Course Schedule (Leetcode #207)

```python
from collections import defaultdict

g = defaultdict(list)
for c, p in prerequisites:
    g[c].append(p)

v = set()

def dfs(c):
    if c in v:
        return False
    if g[c] == []:
        return True
    v.add(c)
    for p in g[c]:
        if not dfs(p):
            return False
    v.remove(c)
    g[c] = []
    return True

for c in range(numCourses):
    if not dfs(c):
        return False
return True
```

---
