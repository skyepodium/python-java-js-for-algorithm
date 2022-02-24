# 1. 설명
- 두수의 hamming distance를 구하세요.


[문제 링크](https://leetcode.com/problems/hamming-distance/)

XOR 연산, bit 개수 사용

# 2. 코드
### 1) python
```python
class Solution:
    def hammingDistance(self, x: int, y: int) -> int:
        return bin(x^y).count("1")
```

### 2) java
```java
class Solution {
    public int hammingDistance(int x, int y) {
        return Integer.bitCount(x ^ y);
    }
}
`