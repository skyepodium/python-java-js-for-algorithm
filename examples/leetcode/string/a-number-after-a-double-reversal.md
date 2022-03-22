# 1. 설명
- 뒤집었을때 0이 앞에 안오는지 여부를 반환하세요.


[문제 링크](https://leetcode.com/problems/a-number-after-a-double-reversal/)


# 2. 코드
### 1) python
```python
class Solution:
    def isSameAfterReversals(self, num: int) -> bool:
        return num == 0 or (num > 0 and num % 10 != 0)
```

### 2) java
```java
class Solution {
    public boolean isSameAfterReversals(int num) {
        return num == 0 || (num > 0 && num % 10 != 0);
    }
}
```

### 3) JavaScript
```js
const isSameAfterReversals = (num) => {
    return num === 0 || (num > 0 && num % 10 !== 0)
};
```