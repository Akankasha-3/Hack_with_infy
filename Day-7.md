# Day-7
__________________________________________________________________

## 1) Number of Events Can Happen (LeetCode #1353)

You are given an array of events where `events[i] = [startDayi, endDayi]`. Every event `i` starts at `startDayi` and ends at `endDayi`.

You can attend an event `i` at any day `d` where `startTimei <= d <= endTimei`. You can only attend one event at any time `d`.

Return the maximum number of events you can attend.

```python
class Solution:
    def maxEvents(self, events: List[List[int]]) -> int:
        events.sort()
        day = 0
        cnt = 0
        heap = []
        i = 0
        while i < len(events) or heap:
            if not heap:
                day = events[i][0]
            while i < len(events) and events[i][0] <= day:
                heapq.heappush(heap, events[i][1])
                i += 1
            heapq.heappop(heap)
            day += 1
            cnt += 1
            while heap and heap[0] < day:
                heapq.heappop(heap)
        return cnt
```

---

## 2) Climbing Stairs (LeetCode #70)

You are climbing a staircase. It takes `n` steps to reach the top.  
Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n < 3:
            return n
        dp = [0] * (n)
        dp[0] = 1
        dp[1] = 2
        for i in range(2, n):
            dp[i] = dp[i - 1] + dp[i - 2]
        return dp[n - 1]
```

**Optimal:**
```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n < 3:
            return n 
        a = 1
        b = 2
        for i in range(2, n):
            c = a + b
            a = b
            b = c
        return b
```

---

## 3) Min Cost Climbing Stairs (LeetCode #746)

You are given an integer array `cost` where `cost[i]` is the cost of `i`th step on a staircase.  
Once you pay the cost, you can either climb one or two steps.  
You can either start from the step with index 0, or the step with index 1.  
Return the minimum cost to reach the top of the floor.

```python
class Solution:
    def minCostClimbingStairs(self, cost: List[int]) -> int:
        dp = [0] * (len(cost) + 1)
        dp[-2] = cost[-1]
        for i in range(len(cost) - 2, -1, -1):
            dp[i] = cost[i] + min(dp[i + 1], dp[i + 2])
        return min(dp[0], dp[1])
```

**Method-2:**
```python
class Solution:
    def minCostClimbingStairs(self, cost: List[int]) -> int:
        b = 0
        a = cost[-1]
        for i in range(len(cost) - 2, -1, -1):
            c = a
            a = cost[i] + min(a, b)
            b = c
        return min(a, b)
```

---

## 4) House Robber (LeetCode #193)

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed,  
the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected  
and it will automatically contact the police if two adjacent houses were broken into on the same night.  
Return the maximum amount of money you can rob tonight without alerting the police.

```python
# Best approach
class Solution:
    def rob(self, nums: List[int]) -> int:
        a, b = 0, 0
        for i in range(len(nums)):
            c = a + nums[i]
            d = max(a, b)
            a = d
            b = c
        return max(a, b)
```

**Or**
```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        a, b = 0, 0
        for i in range(len(nums)):
            c = max(a, b + nums[i])
            b = a
            a = c
        return a  # optimal
```

**DP:**
```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        dp = [0] * len(nums)
        dp[0] = nums[0]
        dp[1] = max(nums[0], nums[1])
        for i in range(2, len(nums)):
            dp[i] = max(dp[i - 1], dp[i - 2] + nums[i])
        return dp[-1]
```

**Recursive:**
```python
def fun(i, n, pr):
    if i >= n:
        return pr
    p = fun(i + 2, n, pr + a[i])
    np = fun(i + 1, n, pr)
    return max(np, p)

a = list(map(int, input().split()))
print(fun(0, len(a), 0))
```
