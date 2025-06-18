## Day-6
___________________________________________________________________

### 1) Print count of palindromic substrings

```python
l = input()
k = 0
i, j = 0, 0
x = 0
while x < len(l):
    i, j = x, x 
    while j < len(l) and i >= 0:
        if l[i] == l[j]:
            k += 1 
            i -= 1 
            j += 1 
        else:
            break
    i, j = x, x + 1
    while j < len(l) and i >= 0 and l[i] == l[j]:
        k += 1 
        i -= 1 
        j += 1
    x += 1
print(k)

# Brute-force method
k = 0
for i in range(2, len(l) + 1):
    for j in range(len(l) - i + 1):
        if l[j:j+i] == l[j:j+i][::-1]:
            k += 1 
print(k + len(l))
```

---

### 2) Print maximum length of palindromic substring

```python
l = input()
k = 0
i, j = 0, 0
x = 0
m = 1
ind = 0
while x < len(l):
    i, j = x, x 
    while j < len(l) and i >= 0:
        if l[i] == l[j]:
            k += 1 
            if j - i + 1 > m:
                m = j - i + 1 
                ind = i
            i -= 1 
            j += 1 
        else:
            break
    i, j = x, x + 1
    while j < len(l) and i >= 0 and l[i] == l[j]:
        k += 1 
        if j - i + 1 > m:
            m = j - i + 1 
            ind = i
        i -= 1 
        j += 1
    x += 1
print(m, l[ind:ind+m])
```

---

### 3) Return the row (0-based index) which contains more number of 0’s

#### Method-1: Brute force - O(n * m)

```python
a, b = map(int, input().split())  # a: columns, b: rows
m, i = float('inf'), -1
for j in range(b):
    v = list(map(int, input().split()))
    for k in range(a):
        if v[k] == 1:
            break
    if k < m and v[-1] == 1:
        m = k
        i = j 
print(i)
```

#### Method-2: Binary search - O(n * log m)

```python
def count_zeros_binary_search(row):
    low, high = 0, len(row) - 1
    while low <= high:
        mid = (low + high) // 2
        if row[mid] == 0:
            high = mid - 1
        else:
            low = mid + 1
    return low  # first 1's index

a, b = map(int, input().split())
max_zeros = -1
row_index = -1
for i in range(b):
    row = list(map(int, input().split()))
    zero_count = count_zeros_binary_search(row)
    if a - zero_count > max_zeros:
        max_zeros = a - zero_count
        row_index = i
print(row_index)
```

#### Method-3: Optimal - O(n + m)

```python
a, b = map(int, input().split())
matrix = [list(map(int, input().split())) for _ in range(b)]

max_row_index = -1
j = 0

# Start from top-right corner
for i in range(b):
    while j < a and matrix[i][j] == 0:
        j += 1
        max_row_index = i
print(max_row_index)
```


### 4) Number of Platforms Required

```python
a = list(map(int, input().split()))  # Arrival times
d = list(map(int, input().split()))  # Departure times

a.sort()
d.sort()

m, c = 0, 0
i, j = 0, 0

while i < len(a) and j < len(d):
    if a[i] <= d[j]:
        c += 1
        m = max(m, c)
        i += 1
    else:
        c -= 1
        j += 1

print(m)
```

