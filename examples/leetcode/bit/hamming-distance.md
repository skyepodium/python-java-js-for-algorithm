# 1. 설명
- 두수의 hamming distance를 구하세요.


[문제 링크](https://leetcode.com/problems/hamming-distance/)

XOR 연산, bit 개수 사용

# 2. 코드
### 1) Python
```python
class Solution:
    def hammingDistance(self, x: int, y: int) -> int:
        return bin(x^y).count("1")
```

### 2) Java
```java
class Solution {
    public int hammingDistance(int x, int y) {
        return Integer.bitCount(x ^ y);
    }
}
```

### 3) JavaScript
```js
const hammingDistance = (x, y) => {

    return (x^y).toString(2)
                .split("")
                .filter(x => x === "1").length
};
```