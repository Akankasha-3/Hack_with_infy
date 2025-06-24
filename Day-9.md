# Day-9

---

## 1. Maximum Number of Events That Can Be Attended II (LeetCode #1751)

### For Exactly `k` Events

```python
n = int(input())
l = []
for _ in range(n):
    l.append(list(map(int, input().split())))
l.sort()
k = int(input())
d = []
p = [1] * n
h = [1] * n
for i in l:
    d.append(i[-1])
print(d)
for i in range(1, n):
    j = 0
    m = float('-inf')
    f = 0
    while j < i:
        if l[j][1] <= l[i][0]:
            if d[j] + l[i][2] > d[i]:
                d[i] = d[j] + l[i][2]
                f = 1
                m = max(m, p[j])
        j += 1
    if f:
        p[i] = m + p[i]
m = 0
for i in range(n):
    if p[i] == k:
        m = max(m, d[i])
print(m)
```

### For At Most `k` Events

```python
for i in range(n):
    if p[i] <= k:
        m = max(m, d[i])
print(m)
```

---

## 2. Can Reach the Last Cell in Grid (Path Exists)

```python
def can(i, j, m, n):
    if i >= m or j >= n:
        return 0
    if i == m - 1 and j == n - 1:
        return 0 if l[-1][-1] == 0 else 1
    if j + 1 < n and i + 1 < m and l[i][j + 1] == 1 and l[i + 1][j] == 1:
        return can(i, j + 1, m, n) or can(i + 1, j, m, n)
    if j + 1 < n and l[i][j + 1] == 1:
        return can(i, j + 1, m, n)
    if i + 1 < m and l[i + 1][j] == 1:
        return can(i + 1, j, m, n)
    return 0

m, n = map(int, input().split())
l = [list(map(int, input().split())) for _ in range(m)]
print(can(0, 0, m, n))
```

---

## 3. Number of Paths (From Top-Left to Bottom-Right)

```python
def can(i, j, m, n):
    if i >= m or j >= n or l[i][j] == 0:
        return 0
    if i == m - 1 and j == n - 1:
        return 1
    return can(i, j + 1, m, n) + can(i + 1, j, m, n)

m, n = map(int, input().split())
l = [list(map(int, input().split())) for _ in range(m)]
print(0 if l[0][0] == 0 or l[m - 1][n - 1] == 0 else can(0, 0, m, n))
```

---

## 4. Number of Islands (LeetCode #200)

```python
def grid(i, j):
    if i < 0 or j < 0 or i >= m or j >= n or l[i][j] != 1:
        return
    l[i][j] = 3
    grid(i + 1, j)
    grid(i - 1, j)
    grid(i, j + 1)
    grid(i, j - 1)

m, n = map(int, input().split())
l = [list(map(int, input().split())) for _ in range(m)]
k = 0
for i in range(m):
    for j in range(n):
        if l[i][j] == 1:
            k += 1
            grid(i, j)
print(k)
```
