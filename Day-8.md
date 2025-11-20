# Day-8
---

## 1) Coin Change Problem

### Approach 1: 1D DP (Optimal)

```python
l = list(map(int, input().split()))
k = int(input())
dp = [0] * (k + 1)
dp[0] = 1
for i in range(1, k + 1):
    for j in l:
        if i - j > 0:
            dp[i] = dp[i - j]
        elif i == j:
            dp[i] = 1
        else:
            dp[i] = dp[j]
    print(dp)
print('Yes' if dp[-1] != 0 else 'no')
```

### Approach 2: 2D DP

```python
n = int(input())
l = list(map(int, input().split()))
k = int(input())
dp = [[0] * (k + 1) for _ in range(n + 1)]
for j in range(n + 1):
    dp[j][0] = 1
for i in range(1, n + 1):
    for j in range(1, k + 1):
        if j - l[i - 1] >= 0:
            dp[i][j] = dp[i - 1][j] or dp[i - 1][j - l[i - 1]]
        else:
            dp[i][j] = dp[i - 1][j]
print(1 if dp[-1][-1] else -1)
```

**Input:**  
`2 8 4 3`  
`16`  
**Output:** `-1`  

**Input:**  
`2 8 4 3`
`12`  
**Output:** `1`  

---

## 2) Minimum Number of Coins to Generate N (Return -1 if not possible)

### Approach 1: 1D DP (Optimal)

```python
l = list(map(int, input().split()))
k = int(input())
dp = [float('inf')] * (k + 1)
dp[0] = 0
for i in range(1, k + 1):
    for j in l:
        if i - j >= 0:
            dp[i] = min(dp[i], 1 + dp[i - j])
    print(dp)
print(dp[-1] if dp[-1] != float('inf') else -1)
```

### To Print Yes or No (1 if possible, 0 otherwise)

```python
l = list(map(int, input().split()))
k = int(input())
dp = [0] * (k + 1)
dp[0] = 1
for i in range(1, k + 1):
    for j in l:
        if i - j >= 0:
            dp[i] = dp[i] or dp[i - j]
print(dp[-1])
```

### Approach 2: 2D DP

```python
n = int(input())
l = list(map(int, input().split()))
k = int(input())
dp = [[0] * (k + 1) for _ in range(n + 1)]

for j in range(n + 1):
    dp[j][0] = 1
for i in range(1, n + 1):
    for j in range(1, k + 1):
        if j - l[i - 1] > 0:
            dp[i][j] = dp[i - 1][j] or dp[i][j - l[i - 1]]
        elif j < l[i - 1]:
            dp[i][j] = dp[i - 1][j]
        elif j == l[i - 1]:
            dp[i][j] = 1
print(dp[-1][-1])
```

---

## 3) Length of Longest Common Subsequence

```python
a = input()
b = input()
n = len(a) + 1
m = len(b) + 1
dp = [[0] * m for _ in range(n)]
for i in range(1, n):
    for j in range(1, m):
        if a[i - 1] == b[j - 1]:
            dp[i][j] = 1 + dp[i - 1][j - 1]
        else:
            dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
print(dp[-1][-1])
```

### Input:
```
abfgh
acfnh
```

### Output:
```
3
```

### Print the Subsequence

```python
a = input()
b = input()
n = len(a) + 1
m = len(b) + 1
dp = [[0] * m for _ in range(n)]
s = ''
for i in range(1, n):
    for j in range(1, m):
        if a[i - 1] == b[j - 1]:
            dp[i][j] = 1 + dp[i - 1][j - 1]
            s += a[i - 1]
        else:
            dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
print(dp[-1][-1])
print(s)
```

---
length of longest increasing sequence
```python
l=list(map(int,input().split()))
a=[1]*len(l)
for i in range(1,len(l)):
    for j in range(i):
        if l[i]>l[j]:
            a[i]=max(a[i],a[j]+1)
print(max(a))
```
max sum of increasing sequence
```python
l=list(map(int,input().split()))
a=l[:]
for i in range(1,len(l)):
    for j in range(i):
        if l[i]>l[j]:
            a[i]=max(a[i],a[j]+l[i])
print(max(a))
```

## 4) Length of Longest Common Substring

```python
a = input()
b = input()
n = len(a) + 1
m = len(b) + 1
dp = [[0] * m for _ in range(n)]

for i in range(1, n):
    for j in range(1, m):
        if a[i - 1] == b[j - 1]:
            dp[i][j] = 1 + dp[i - 1][j - 1]
        else:
            dp[i][j] = 0
print(dp[-1][-1])
```
