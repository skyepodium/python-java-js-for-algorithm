# 1. 설명
- 계단은 한번에 1칸 또는 2칸을 오를 수 있습니다. 0, 1번째 계단에서 시작할 수 있습니다. 
i 번재 계단을 밟으면 cost[i] 비용이 소모됩니다. n 번째 계단을 밟는 최소 비용을 구하세요.

[문제 링크](https://leetcode.com/problems/min-cost-climbing-stairs/)

# 2. 코드
### 1. tabulation
### 1) python
```python
class Solution:
    def minCostClimbingStairs(self, cost: List[int]) -> int:
        # 1. init
        n = len(cost)
        cost += [0]
        d = [int(1e7)] * (n+1)

        # 2. bottom up
        d[0], d[1] = cost[0], cost[1]
        for i in range(0, n):
            if i + 1 <= n:
                d[i+1] = min(d[i+1], d[i] + cost[i+1])
            if i + 2 <= n:
                d[i+2] = min(d[i+2], d[i] + cost[i+2])

        return d[n]
```

### 2) java
```java
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        // 1. init
        int n = cost.length;
        int[] d = new int[n+1];
        for(int i=0; i<=n; i++) d[i] = Integer.MAX_VALUE;

        // 2. dp - bottom up
        d[0] = cost[0];
        d[1] = cost[1];
        for(int i=0; i<n; i++) {
            if(i+1 <= n) {
                int c = i + 1 >= n ? 0 : cost[i+1];
                d[i+1] = Math.min(d[i+1], d[i] + c);
            }

            if(i+2 <= n) {
                int c = i + 2 >= n ? 0 : cost[i+2];
                d[i+2] = Math.min(d[i+2], d[i] + c);
            }
        }

        return d[n];
    }
}
```

### 3) JavaScript
```js
const minCostClimbingStairs = (cost) => {
    // 1. init
    const n = cost.length
    cost = cost.concat([0])
    const MAX_VAL = 10000001
    const d = Array.from(new Array(n+1)).fill(MAX_VAL)

    // 2. bottom up
    d[0] = cost[0]
    d[1] = cost[1]

    for(let i=0; i<n; i++) {
        if(i + 1 <= n)
            d[i+1] = Math.min(d[i+1], d[i] + cost[i+1])
        if(i + 2 <= n)
            d[i+2] = Math.min(d[i+2], d[i] + cost[i+2])
    }

    return d[n]
};
```

### 2. memoization
### 1) python
```python
class Solution:
    def minCostClimbingStairs(self, cost: List[int]) -> int:
        # 1. init
        n = len(cost)
        cost += [0]
        MAX_VAL = int(1e7)
        d = [MAX_VAL] * (n+1)

        # 2. top down
        d[0], d[1] = cost[0], cost[1]
        def go(i):
            if d[i] < MAX_VAL:
                return d[i]

            if i - 1 >= 0:
                d[i] = min(d[i], go(i-1) + cost[i])
            if i - 2 >= 0:
                d[i] = min(d[i], go(i-2) + cost[i])

            return d[i]

        return go(n)
```

### 2) java
```java
class Solution {
    int[] d;
    int[] cArr;
    int n;
    int maxVal = Integer.MAX_VALUE;
    public int minCostClimbingStairs(int[] cost) {
        // 1. init
        n = cost.length;
        cArr = cost;
        d = new int[n+1];
        for(int i=0; i<=n; i++) d[i] = maxVal;

        // 2. dp - top down
        d[0] = cost[0];
        d[1] = cost[1];

        return go(n);
    }

    public int go(int i) {
        if(d[i] < maxVal) return d[i];

        if(i-1 >= 0) {
            int c = i == n ? 0 : cArr[i];
            d[i] = Math.min(d[i], go(i-1) + c);
        }

        if(i-2 >= 0) {
            int c = i == n ? 0 : cArr[i];
            d[i] = Math.min(d[i], go(i-2) + c);
        }

        return d[i];
    }
}
```

### 3) JavaScript
```js
const minCostClimbingStairs = (cost) => {
    // 1. init
    const n = cost.length
    cost = cost.concat([0])
    const MAX_VAL = 10000001
    const d = Array.from(new Array(n+1)).fill(MAX_VAL)

    // 2. top down
    d[0] = cost[0]
    d[1] = cost[1]

    const go = (i) => {
        if(d[i] < MAX_VAL) return d[i]

        if(i - 1 >= 0)
            d[i] = Math.min(d[i], go(i-1) + cost[i])
        if(i - 2 >= 0)
            d[i] = Math.min(d[i], go(i-2) + cost[i])

        return d[i]
    }

    return go(n)
};
```