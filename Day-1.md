# 📘 DAY-1: Python Practice Problems

---

### 1️⃣ Sum of Integers in Range `n`

```python
n = int(input())
print((n * (n + 1)) // 2)
```

---

### 2️⃣ Sum of Even Numbers within the Range `n`

```python
n = int(input())
l = sum(range(2, n + 1, 2))
print(l)
```

---

### 3️⃣ Prime or Not

```python
n = int(input())
k = False
for i in range(2, int(n**0.5) + 1):
    if n % i == 0:
        k = True
        break
print('prime' if not k and n >= 2 else 'Not prime')
```

---

### 4️⃣ Print Array Elements Without Repetition

**Naive approach – O(n²):**

```python
l = list(map(int, input().split()))
d = []
for i in l:
    if i not in d:
        d.append(i)
print(*d)
```

**Optimal approach – O(n):**

```python
l = list(map(int, input().split()))
d = []
s = set()
for i in l:
    if i not in s:
        s.add(i)
        d.append(i)
print(*d)
```

---

### 5️⃣ Print Each Element and Its Frequency Uniquely

```python
from collections import Counter

l = list(map(int, input().split()))
d = Counter(l)
print(*(list(d.items())))
```

---

### 6️⃣ Print the First Non-Repeating Element

**Method 1:**

```python
from collections import Counter

l = list(map(int, input().split()))
d = Counter(l)
for i, j in d.items():
    if j == 1:
        print(i)
        break
```

**Method 2 (Best – using XOR):**

```python
l = list(map(int, input().split()))
x = 0
for i in l:
    x ^= i
print(x)
```

> 🔎 Try using **binary search** if the array is sorted.

---

### 7️⃣ Check if the `k`th Rightmost Bit is Set or Unset

```python
n = int(input())
k = int(input())
if n ^ (2 ** k) < n:
    print('set')
else:
    print('unset')
```

---

### 8️⃣ XOR of All the Elements in the Range `n`

```python
n = int(input())
if n % 4 == 0:
    print(n)
elif n % 4 == 3:
    print(0)
elif n % 4 == 2:
    print(n + 1)
else:
    print(1)
```
