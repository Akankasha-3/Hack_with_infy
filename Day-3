Day-3  
___________________________________________________________________  

**Binary Search**  

1) Given a sorted array and a key, if the key is found return -1 else return number of elements less than the key.  
```python
def bs(a, ke):
    i = 0
    j = len(a) - 1
    while i <= j:
        k = (i + j) // 2
        if a[k] == ke:
            return -1
        elif a[k] > ke:
            j = k - 1
        else:
            i = k + 1
    return i

a = list(map(int, input().split()))
k = int(input())
print(bs(a, k))
```

2) **Koko Eating Bananas:**  
Koko loves to eat bananas. There are n piles of bananas, the ith pile has piles[i] bananas. The guards have gone and will come back in h hours.  
Koko can decide her bananas-per-hour eating speed of k. Each hour, she chooses some pile of bananas and eats k bananas from that pile.  
If the pile has less than k bananas, she eats all of them instead and will not eat any more bananas during this hour.  
Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.  
Return the minimum integer k such that she can eat all the bananas within h hours.  
```python
import math

def koko(a, k):
    if sum(a) <= k:
        return 1
    i, j = 2, max(a)
    g = j
    while i <= j:
        m = (i + j) // 2
        c = sum([math.ceil(d / m) for d in a])
        if c <= k:
            g = m
            j = m - 1
        else:
            i = m + 1
    return g

l = list(map(int, input().split()))
k = int(input())
print(koko(l, k))
```

3) **Aggressive Cows:**  
You are given an array with unique elements of stalls[], which denote the position of a stall.  
You are also given an integer k which denotes the number of aggressive cows.  
Your task is to assign stalls to k cows such that the minimum distance between any two of them is the maximum possible.  
```python
class Solution:
    def aggressiveCows(self, stalls, k):
        def can(s, k, d):
            c = 1
            last_position = s[0]
            for j in range(1, len(s)):
                if s[j] - last_position >= d:
                    c += 1
                    last_position = s[j]
                if c == k:
                    return 1
            return 0

        stalls.sort()
        l, h = 1, stalls[-1] - stalls[0]
        r = 0

        while l <= h:
            m = (l + h) // 2
            if can(stalls, k, m) == 1:
                r = m
                l = m + 1
            else:
                h = m - 1
        
        return r
```

4) **Peak Element**  
```python
nums = list(map(int, input().split()))
i, j = 0, len(nums) - 1
while i < j:
    k = (i + j) // 2
    if nums[k] > nums[k + 1]:
        j = k
    else:
        i = k + 1
print(i)
```

**RECURSION**  
```python
import sys
sys.setrecursionlimit(2000)
```
# Allows 2000 recursion calls instead of 999 calls

5) **Sum of Elements**  
```python
def su(a, i, n):
    if i < n:
        return a[i] + su(a, i + 1, n)
    else:
        return 0

n = int(input())
l = list(map(int, input().split()))
print(su(l, 0, n))
```

6) **Sum of Even Elements**  
```python
def su(a, i, n):
    if i < n:
        if a[i] % 2 == 0:
            return a[i] + su(a, i + 1, n)
        else:
            return su(a, i + 1, n)
    else:
        return 0

n = int(input())
l = list(map(int, input().split()))
print(su(l, 0, n))
```
