# 1. 설명
- i번째, j번째 지점의 차이의 최대값을 구하세요.
- i < j

- 배열의 길이 1 <= n <= 10만



[문제 링크](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

# 2. 코드
### 1) python
```python
class Solution:
    def maxProfit(self, prices: list[int]) -> int:
        result = 0
        min_val = 10000

        for price in prices:
            # 1. 현재 지점까지의 최소값 매번 갱신
            min_val = min(min_val, price)

            # 2. 최소값의 차이 갱신
            result = max(result, price - min_val)

        return result
```

### 2) java
```java
class Solution {
    public int maxProfit(int[] prices) {
        int minVal = 10000;
        int result = 0;

        for(int num: prices) {
            // 1 현재 지점까지의 최소값 갱신
            minVal = Math.min(minVal, num);
            // 2. 현재의 값고 최소값 차이의 최대값 갱신
            result = Math.max(result, num - minVal);
        }

        return result;
    }
}
```