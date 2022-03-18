# 1. 설명
- 정수 n을 k진법으로 변환하고 각 자리수의 합을 반환하세요


[문제 링크](https://leetcode.com/problems/sum-of-digits-in-base-k)

# 2. 코드
### 1) python
```python
class Solution:
    def sumBase(self, n: int, k: int) -> int:
        # 1. init
        res = 0

        # 2. loop
        while n > 0:
            res += n % k
            n //= k

        return res
```
### 2) java
```java
class Solution {
    public int sumBase(int n, int k) {
        // 1. init
        int res = 0;

        // 2. loop
        while(n > 0) {
            res += n%k;
            n /= k;
        }

        return res;
    }
}
```

### 3) JavaScript
```js
var sumBase = function(n, k) {
    // 1. init
    let res = 0

    // 2. loop
    while(n > 0) {
        res += n % k
        n = Math.floor(n/k)
    }

    return res
};
```