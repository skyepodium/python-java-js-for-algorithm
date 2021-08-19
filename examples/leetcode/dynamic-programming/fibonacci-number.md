# 1. 설명
- 피보나치 수를 반환하세요.

[문제 링크](https://leetcode.com/problems/fibonacci-number/)

# 2. 코드
### 1) python
```python
class Solution:
    def fib(self, n: int) -> int:
        
        if n < 2:
            return n
        
        d = [0 for _ in range(n+1)]
        
        d[0] = 0
        d[1] = 1
        for i in range(2, n+1):
            d[i] = d[i-1] + d[i-2]
            
        return d[n]
```

### 2) java
```java
class Solution {
    public int fib(int n) {
        
        if(n < 2) return n;
        
        int[] d = new int[n+1];

        d[0] = 0;
        d[1] = 1;
        for(int i=2; i<=n; i++) {
            d[i] = d[i-1] + d[i-2];
        }
        
        return d[n];
    }
}
```