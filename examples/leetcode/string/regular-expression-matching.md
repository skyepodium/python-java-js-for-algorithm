# 1. 설명
- 원래는 정규표현식 문자열 매치를 구현하는 문제입니다.


[문제 링크](https://leetcode.com/problems/regular-expression-matching/)


# 2. 코드
### 1) Python
```python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:

        return re.fullmatch(re.sub("\\.", "[a-z]", p), s) is not None
```

### 2) Java
```java
class Solution {
    public boolean isMatch(String s, String p) {
        return s.matches(p.replaceAll("\\.", "[a-z]"));
    }
}
```

### 3) JavaScript
```js
const isMatch = (s, p) => {
    return s.match(new RegExp(`^${p.replace(/\\./g, "[a-z]")}$`, 'g')) !== null
};
```