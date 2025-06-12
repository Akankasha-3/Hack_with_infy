DAY-2  
___________________________________________________________________

1) Two sum (print the pair that sums to the target)

```python
l = list(map(int, input().split()))
target = int(input())
d = {}
for i in range(len(l)):
    d[l[i]] = i
k = -1
for i in l:
    if target - i in d:
        k = [i, target - i]
        break
print(k)
```

2) Reverse the order of alphabets without changing the positions of special characters

**Best case: O(n/2)**

```python
l = input()
s = list(l)
i, j = 0, len(s) - 1
while i <= j:
    if 'a' <= s[i] <= 'z' and 'a' <= s[j] <= 'z':
        s[i], s[j] = s[j], s[i]
        i += 1
        j -= 1
    if not 'a' <= s[i] <= 'z':
        i += 1
    if not 'a' <= s[j] <= 'z':
        j -= 1
print(''.join(s))
```

**Brute force: O(2n)**

```python
l = input()
p = []
for i in l:
    if 'a' <= i <= 'z':
        p.append(i)
p = p[::-1]
for i in range(len(l)):
    if not 'a' <= l[i] <= 'z':
        p.insert(i, l[i])
print(''.join(p))
```

3) Sliding window: Maximum sum can be obtained by using k consecutive elements

```python
l = list(map(int, input().split()))
k = int(input())
p = sum(l[:k])
m = 0
for i in range(1, len(l) - k + 1):
    p = p - l[i - 1] + l[i + k - 1]
    m = max(m, p)
print(m)

# Input: 10 3 1 11 2 4 6 8 5 10 3
# k = 4
# Output: 29
```

4) Max count of odd elements in any subarray of length k

```python
l = list(map(int, input().split()))
k = int(input())
c = 0
for i in range(k):
    if l[i] & 1 == 0:
        c += 1
q = c
for i in range(1, len(l) - k + 1):
    if l[i - 1] & 1 == 1:
        c -= 1
    if l[i + k - 1] & 1 == 1:
        c += 1
    q = max(q, c)
print(q)
```

5) Maximum sum of k-cards; only remove card if and only if the previous one is removed

```python
l = list(map(int, input().split()))
k = int(input())
p = l[-k:] + l[:k]
s = sum(p[:k])
m = s
for i in range(1, len(p) - k + 1):
    s = s - p[i - 1] + p[i + k - 1]
    m = max(m, s)
print(m)

# Note: Below code fails for optimal solution

# s = sum(l[k:])
# p = sum(l)
# q = sum(l)
# m = s
# for i in range(k):
#     if l[-1] > l[0]:
#         p -= l[-1]
#         l.pop(-1)
#     else:
#         p -= l[0]
#         l.pop(0)
#     s = min(m, p)
# print(q - s)
```

6) Length of the longest subarray whose sum is ≤ k

```python
l = list(map(int, input().split()))
k = int(input())
s = sum(l)
if s <= k:
    print(len(l))
else:
    h = len(l)
    i, j = 0, len(l) - 1
    while i < j:
        if l[i] > l[j]:
            s -= l[i]
            if s <= k:
                print(h - 1)
                break
            else:
                h -= 1
                i += 1
        else:
            s -= l[j]
            if s <= k:
                print(h - 1)
                break
            else:
                h -= 1
                j -= 1
```

7) Length of longest substring with non-repeating characters

```python
s = input()
m = 1
st = {s[0]: 0}
i, j = 0, 1
while i < j and j < len(s):
    if s[j] not in st:
        st[s[j]] = j
        m = max(m, j - i)
        j += 1
    else:
        if st[s[j]] < i:
            st[s[j]] = j
        else:
            i = st[s[j]] + 1
            st[s[j]] = j
        m = max(m, j - i)
        j += 1
print(m + 1)

# Input: abcdaefckjibes -> Output: 9
# Input: abcdefgabn     -> Output: 8
```

8) Longest subarray with consecutive 1's in a binary list where you can flip at most k elements

```python
l = list(map(int, input().split()))
a = int(input())
z, o = 0, 0
i, j = 0, 0
while j < len(l):
    if z <= a:
        if l[j] == 0:
            z += 1
        j += 1
    else:
        i += 1
        j += 1
        if l[i] == 0:
            z -= 0
    o = max(o, j - i)
print(o)
```
