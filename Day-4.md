# Day-4
---

## PREFIX SUM

### 1) Range Sum Queries (1-based Index)

```python
a, b = map(int, input().split())
l = list(map(int, input().split()))
m = l[0]
z = [m]
for j in range(1, a):
    m += l[j]
    z.append(m)

for i in range(b):
    x, y = map(int, input().split())
    if x == 1:
        print(z[y - 1])
    else:
        print(z[y - 1] - z[x - 2])
```

**Time Complexity:** O(1) per query  
**Input:**
```
7 3
2 5 6 1 3 4 2
2 5
3 7
1 6
```
**Output:**
```
15
16
21
```

---

## SEGMENT TREE

### Conditions:
- `curr = l, r` (segment)
- `asked = s, e`

**Three cases:**
1. Completely out: `if r < s or l > e` → return 0  
2. Completely in: `if l >= s and r <= e` → return segment value  
3. Overlap: `m = (l + r) // 2`  
   → return combined result of left and right child

---

### 2) Max Element Within the Range Using Prefix + Segment Tree

```python
a, b = map(int, input().split())
l = list(map(int, input().split()))
m = l[0]
z = [m]
for j in range(1, a):
    m += l[j]
    z.append(m)

print(z)
for i in range(b):
    x, y = map(int, input().split())
    print(max(l[x - 1:y]))
```

> If update queries are needed, use segment tree instead.

---

### Segment Tree with Update Support

```python
def build_tree(l, r, ind, k, m):
    if l == r and l == m:
        p[l] += k
        st[ind] = p[l]
        return
    else:
        m = (l + r) // 2
        build_tree(l, m, 2 * ind + 1)
        build_tree(m + 1, r, 2 * ind + 2)
        st[ind] = (st[2 * ind + 1] + st[2 * ind + 2])
```

> Uses more space → we shift to Fenwick Tree

---

## Segment Tree Creation

```python
def build_tree(l, r, ind):
    if l == r:
        s[ind] = p[l]
        return
    else:
        m = (l + r) // 2
        build_tree(l, m, 2 * ind + 1)
        build_tree(m + 1, r, 2 * ind + 2)
        s[ind] = max(s[2 * ind + 1], s[2 * ind + 2])

p = list(map(int, input().split()))
s = [0] * (4 * len(p))
build_tree(0, len(p) - 1, 0)
print(s)
```

---

### 3) Optimized Max Element Query

```python
def build_tree(l, r, ind):
    if l == r:
        st[ind] = p[l]
        return
    else:
        m = (l + r) // 2
        build_tree(l, m, 2 * ind + 1)
        build_tree(m + 1, r, 2 * ind + 2)
        st[ind] = max(st[2 * ind + 1], st[2 * ind + 2])

def maxi(l, r, i, s, e):
    if r < s or l > e: return 0
    elif l >= s and r <= e: return st[i]
    else:
        m = (l + r) // 2
        return max(maxi(l, m, 2 * i + 1, s, e), maxi(m + 1, r, 2 * i + 2, s, e))

p = list(map(int, input().split()))
st = [0] * (4 * len(p))
build_tree(0, len(p) - 1, 0)
q = int(input())
for i in range(q):
    x, y = map(int, input().split())
    print(maxi(0, len(p) - 1, 0, x - 1, y - 1))
```

---

### 4) Minimum Element Query

```python
def build_tree(l, r, ind):
    if l == r:
        st[ind] = p[l]
        return
    else:
        m = (l + r) // 2
        build_tree(l, m, 2 * ind + 1)
        build_tree(m + 1, r, 2 * ind + 2)
        st[ind] = min(st[2 * ind + 1], st[2 * ind + 2])

def maxi(l, r, i, s, e):
    if r < s or l > e: return float('inf')
    elif l >= s and r <= e: return st[i]
    else:
        m = (l + r) // 2
        return min(maxi(l, m, 2 * i + 1, s, e), maxi(m + 1, r, 2 * i + 2, s, e))

p = list(map(int, input().split()))
st = [float('inf')] * (4 * len(p))
build_tree(0, len(p) - 1, 0)
q = int(input())
for i in range(q):
    x, y = map(int, input().split())
    print(maxi(0, len(p) - 1, 0, x - 1, y - 1))
```

---

### 5) Sum Within Range

```python
def build_tree(l, r, ind):
    if l == r:
        st[ind] = p[l]
        return
    else:
        m = (l + r) // 2
        build_tree(l, m, 2 * ind + 1)
        build_tree(m + 1, r, 2 * ind + 2)
        st[ind] = (st[2 * ind + 1] + st[2 * ind + 2])

def maxi(l, r, i, s, e):
    if r < s or l > e: return 0
    elif l >= s and r <= e: return st[i]
    else:
        m = (l + r) // 2
        return maxi(l, m, 2 * i + 1, s, e) + maxi(m + 1, r, 2 * i + 2, s, e)

p = list(map(int, input().split()))
st = [0] * (4 * len(p))
build_tree(0, len(p) - 1, 0)
q = int(input())
for i in range(q):
    x, y = map(int, input().split())
    print(maxi(0, len(p) - 1, 0, x - 1, y - 1))
```

---

### 6) Fenwick Tree (BIT) with Update and Range Sum Queries

```python
def create(i, x):
    while i < len(l):
        l[i] += x
        i += (i & -i)

def prefix_sum(i):
    s = 0
    while i > 0:
        s += l[i]
        i -= (i & -i)
    return s

n = int(input())
p = list(map(int, input().split()))
l = [0] * (n + 1)
for i in range(n):
    create(i + 1, p[i])

n_q = int(input())
for i in range(n_q):
    a, b, c = map(int, input().split())
    if a == 2:
        create(b, c)
    else:
        print(prefix_sum(c) - prefix_sum(b - 1))
```

**Input:**
```
5
1 4 3 6 2
3
1 2 4
2 3 5
1 2 4
```

**Output:**
```
13
18
```

---
