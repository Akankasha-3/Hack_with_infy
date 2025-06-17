# Day-5
---

## 1) Fenwick Tree without using any pre intake of list

```python
def create(i):
    while(i < n):
        l[i] = l[i] + z
        i = i + (i & -i)

def su(i):
    s = 0
    while(i > 0):
        s += l[i]
        i = i - (i & -i)
    return s

a, n = map(int, input().split())
n += 1
l = [0] * n 
for _ in range(a):
    x, y, z = map(int, input().split())
    if x == 1:
        create(y)  # update query
    else:
        print(su(z) - su(y - 1))
```

## 2) Second Largest Element

```python
n = int(input())
l = list(map(int, input().split()))
s, f = 0, 0
for i in range(n):
    if f < l[i]:
        s = f
        f = l[i]
    else:
        if s < l[i] and l[i] != f:
            s = l[i]
print(s)
```

## 3) Element with Largest Frequency

```python
n = int(input())
l = list(map(int, input().split()))
d = {}
m = 1 
t = -1
for i in l:
    if i not in d:
        d[i] = 1 
    else:
        d[i] += 1 
        if m < d[i]:
            t = i 
print(t)
```

## 4) Second Largest Frequency Element

```python
n = int(input())
l = list(map(int, input().split()))
d = {}
m = 1 
t = l[0]
sf = 0
se = 0
for i in l:
    if i not in d:
        d[i] = 1 
    else:
        d[i] += 1 
        if m < d[i]:
            sf = m
            se = t
            t = i 
        else:
            if sf != m and sf > d[i]:
                se = i
print(se)
```

## 5) Print Elements Based on Frequency (Lowest to Highest)

Efficient when the values are large.

Input:
```
1 2 2 4 3 3 4 3 4 4
```

Output:
```
1 2 2 3 3 3 4 4 4 4
```

```python
l = list(map(int, input().split()))
d = {}
for i in l:
    if i not in d:
        d[i] = 1 
    else:
        d[i] += 1 
d = dict(sorted(d.items(), key=lambda x: x[1]))
p = []
for i, j in d.items():
    p += [i] * j
print(*p)
```

Alternate sort:
```python
# l.sort(key=lambda x:(d[x], x))  # increasing order
# l.sort(key=lambda x:(d[x], -x)) # decreasing order
```

---

# BUCKET SORT

## 6) Frequency-Based Sorting

Efficient when values are within range(n)

```python
l = list(map(int, input().split()))
d = {}
for i in l:
    if i not in d:
        d[i] = 1 
    else:
        d[i] += 1 

a = [0] * (max(d.values()) + 1)
for i, j in d.items():
    a[j] = i 

for i in range(len(a)):
    if a[i] != 0:
        print(*([a[i]] * i), end=' ')
```

---

## 7) K-Largest Frequency Element

```python
l = list(map(int, input().split()))
d = {}
for i in l:
    if i not in d:
        d[i] = 1 
    else:
        d[i] += 1 

a = [0] * (max(d.values()) + 1)
for i, j in d.items():
    a[j] = i 

for i in range(len(a)):
    if a[i] != 0:
        print(*([a[i]] * i), end=' ')
print()
k = int(input())
for i in range(len(a) - 1, -1, -1):
    if a[i] != 0:
        k -= 1
        if k == 0:
            print(a[i])
            break
```

---

## 8) Gas Stations

### Method 1:

```python
def can():
    if l[0] == 0:
        return False
    else:
        i = 0
        k = l[0]
        while True:
            if len(l) - i <= k or i == len(l) - 1:
                return True
            m = max(l[i + 1:i + k + 1])
            if m == 0:
                return False
            i = i + l[i + 1:].index(m) + 1
            k = l[i]
    return False

l = list(map(int, input().split()))
print(can())
```

### Method 2: Optimal

```python
def canGo():
    k = 0
    for i in nums:
        if k < 0:
            return False
        elif i > k:
            k = i
        k -= 1
    return True

nums = list(map(int, input().split()))
print(canGo())
```

Examples:

Input: `3 2 1 0 4`  
Output: `False`

Input: `2 3 1 1 4`  
Output: `True`

---

## 9) Min Jumps to Reach Last Element (Jump 1/2/3 steps)

```python
def can():
    i, j = 0, 0
    while True:
        if i + 3 < len(l) and l[i + 3] != 0:
            i += 3
            j += 1 
        if i + 2 < len(l) and l[i + 2] != 0:
            i += 2
            j += 1 
        if i + 1 < len(l) and l[i + 1] != 0:
            i += 1
            j += 1 
        if i == len(l) - 1:
            return j

l = list(map(int, input().split()))
print(can())
```

---

## 10) Minimum Steps (Any Step Size)

```python
def can():
    res = 0
    l = r = 0
    while r < len(nums) - 1:
        far = 0
        for i in range(l, r + 1):
            far = max(far, nums[i] + i)
        l = r + 1
        r = far
        res += 1
    return res

nums = list(map(int, input().split()))
print(can())
```

Example:

Input:  
```
3 2 3 1 2 5 3 1 1 2 1 4 6
```

Output:  
```
5
```

---

## 11) Maximum Number of Meetings in a Room

You are given timings of `n` meetings in the form of `(start[i], end[i])`. Return the maximum number of meetings that can be accommodated in a single room.  
Note: Start time of one meeting **cannot be equal** to end time of another.

**Example:**

Input:  
```
start[] = [1, 3, 0, 5, 8, 5]
end[] =   [2, 4, 6, 7, 9, 9]
```

Output:  
```
4
```

Explanation: Meetings = (1, 2), (3, 4), (5, 7), (8, 9)

```python
def maxMeet():
    l = []
    for i in range(len(start)):
        l.append([start[i], end[i]])
    l.sort(key=lambda x: x[1])
    k = 1
    a = l[0]
    for i in l[1:]:
        if a[1] < i[0]:
            k += 1
            a = i
    return k

start = list(map(int, input().split()))
end = list(map(int, input().split()))
print(maxMeet())
```
