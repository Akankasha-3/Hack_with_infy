# Day-10

---

## 🔤 Word Search in Grid (Non-Diagonal Only)

```python
def call(i, j, idx):
    if idx == len(k):
        return True
    if i < 0 or j < 0 or i >= n or j >= m or l[i][j] != k[idx]:
        return False

    temp = l[i][j]
    l[i][j] = '#'
    found = (
        call(i, j + 1, idx + 1) or
        call(i, j - 1, idx + 1) or
        call(i + 1, j, idx + 1) or
        call(i - 1, j, idx + 1)
    )
    l[i][j] = temp
    return found

l = [
    ['A', 'S', 'E', 'T'],
    ['K', 'E', 'T', 'S'],
    ['O', 'E', 'S', 'O'],
    ['P', 'O', 'S', 'T']
]
n = len(l)
m = len(l[0])
k = "SEEK"
found = False

for i in range(n):
    for j in range(m):
        if call(i, j, 0):
            found = True
            break
print("YES" if found else "NO")
```

---

## 🌐 Graphs

### 1. Convert to Adjacency List using Dictionary

```python
from collections import defaultdict

edges = [(2,4), (2,7), (2,8), (7,8), (4,7), (4,10), (8,10), (7,4)]
graph = defaultdict(list)
for i, j in edges:
    graph[i].append(j)
    graph[j].append(i)
```

---

### 2. Print All Paths from `s` to `d`

```python
def paths(s, d):
    v.append(s)
    if s == d:
        print(v)
        v.pop()
        return
    for i in graph[s]:
        if i not in v:
            paths(i, d)
    v.pop()

v = []
paths(2, 10)
```

---

### 3. Count Total Number of Paths

```python
def paths(s, d, k):
    v.add(s)
    if s == d:
        k += 1
        print(v)
        v.remove(s)
        return k
    for i in graph[s]:
        if i not in v:
            k = paths(i, d, k)
    v.remove(s)
    return k

v = set()
print(paths(2, 10, 0))
```

#### Output
```
{2, 4, 7, 8, 10}
{2, 4, 10}
{2, 7, 8, 10}
{2, 4, 7, 10}
{2, 4, 7, 8, 10}
{2, 8, 10}
6
```

---

### 4. Check if Path Exists (DFS)

```python
def paths(s, x):
    v.add(s)
    if s == x:
        return True
    for i in graph[s]:
        if i not in v:
            if paths(i, x): return True
    return False

v = set()
print(paths(2, 7))
```

---

### 5. Sum of Nodes in a Graph

```python
def paths(s):
    v.add(s)
    total = s
    for i in graph[s]:
        if i not in v:
            total += paths(i)
    return total

v = set()
print(paths(2))
```

#### Output
```
31
```

---

### 6. Print Path and Length

```python
def paths(s, d, c=1):
    v.add(s)
    if s == d:
        print(v, c)
        v.remove(d)
        return
    for i in graph[s]:
        if i not in v:
            c += 1
            paths(i, d, c)
            c -= 1
    v.remove(s)

v = set()
print(paths(2, 10))
```

#### Output
```
{2, 4, 7, 8, 10} 5
{2, 4, 10} 3
{2, 7, 8, 10} 4
{2, 4, 7, 10} 4
{2, 4, 7, 8, 10} 5
{2, 8, 10} 3
```

---

### 7. Weighted Graph Paths

```python
def paths(s, d, cost=0):
    v.add(s)
    if s == d:
        print(v, cost)
        v.remove(d)
        return
    for i, w in graph[s]:
        if i not in v:
            cost += w
            paths(i, d, cost)
            cost -= w
    v.remove(s)

edges = [(2,4,2), (2,7,3), (2,8,1), (7,8,1), (7,4,2), (4,10,4), (8,10,2)]
graph = defaultdict(list)
for i, j, w in edges:
    graph[i].append((j, w))
    graph[j].append((i, w))

v = set()
print(paths(2, 10))
```

#### Output
```
{2, 4, 7, 8, 10} 7
{2, 4, 10} 6
{2, 7, 8, 10} 6
{2, 4, 7, 10} 9
{2, 4, 7, 8, 10} 8
{2, 8, 10} 3
```

---

### 8. Breadth First Search (BFS)

```python
edges = [(2,4,2), (2,7,3), (2,8,1), (7,8,1), (7,4,2), (4,10,4), (8,10,1)]
graph = defaultdict(list)
for i, j, w in edges:
    graph[i].append((j, w))
    graph[j].append((i, w))

v = []
q = [2]
while q:
    curr = q.pop()
    for i, w in graph[curr]:
        if i not in v and i not in q:
            q.append(i)
    v.append(curr)

print(v)
```

#### Output
```
[2, 8, 10, 7, 4]
```
