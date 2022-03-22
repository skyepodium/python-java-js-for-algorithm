# 1. 설명
- 모든 a가 나오고 b가 출현했는지 여부를 반환하세요.


[문제 링크](https://leetcode.com/problems/check-if-all-as-appears-before-all-bs/)


# 2. 코드
### 1) python
```python
class Solution:
    def checkString(self, s: str) -> bool:
        return "ba" not in s
```

### 2) java
```java
class Solution {
    public boolean checkString(String s) {
        return !s.contains("ba");
    }
}
```

### 3) JavaScript
```js
const checkString = (s) => {
    return s.indexOf("ba") === -1
};
```