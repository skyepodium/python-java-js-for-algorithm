# 1. 설명
- 세그먼트의 개수를 구하세요


[문제 링크](https://leetcode.com/problems/number-of-segments-in-a-string/)


# 2. 코드
### 1) python
```python
class Solution:
    def countSegments(self, s: str) -> int:
        if s.strip() == "": return 0

        return len(re.split(" +", s.strip()))
```

### 2) java
```java
class Solution {
    public int countSegments(String s) {
        if("".equals(s.trim())) return 0;

        return s.trim().split(" +").length;
    }
}
```

### 3) JavaScript
```js
const countSegments = (s) => {
    if(s.trim() === '') return 0

    return s.trim().split(/ +/).length
};
```