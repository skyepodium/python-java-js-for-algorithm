# 1. 설명
- 계단은 한번에 1칸 또는 2칸을 오를 수 있습니다. n번째 계단을 밟는 경우의 수를 구하세요.

[문제 링크](https://leetcode.com/problems/climbing-stairs/)

# 2. 코드
### 1. tabulation
### 1) python
```python
class Solution:
    def climbStairs(self, n: int) -> int:

        if n <= 2: return n

        d = [0 for _ in range(n + 1)]

        d[0] = 0
        d[1] = 1
        d[2] = 2

        for i in range(3, n + 1):
            d[i] = d[i - 1] + d[i - 2]

        return d[n]   
```

### 2) java
```java
class Solution {
    public int climbStairs(int n) {

        if (n <= 2) return n;

        int[] d = new int[n+1];

        d[0] = 0;
        d[1] = 1;
        d[2] = 2;

        for(int i=3; i<=n; i++) {
            d[i] = d[i-1] + d[i-2];
        }
        return d[n];
    }
}
```

### 2. memoization
### 1) python
```python
class Solution:
    def climbStairs(self, n: int) -> int:

        d = [0 for _ in range(n+1)]
        
        def go(i):
            if i <= 2:
                return i
            
            if d[i] > 0:
                return d[i]
            
            d[i] = go(i-2) + go(i-1)
            
            return d[i]
        
        return go(n)  
```

### 2) java
```java
class Solution {
    int d[];
    public int climbStairs(int n) {
        d = new int[n+1];

        return go(n);
    }

    public int go(int i) {
        if(i <= 2) return i;

        if(d[i] > 0) return d[i];

        d[i] = go(i-2) + go(i-1);

        return d[i];
    }
}
```