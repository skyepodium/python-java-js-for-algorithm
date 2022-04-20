# 1. 설명
- 가장 단어가 많은 문장의 길이를 구하세요

[문제 링크](https://leetcode.com/problems/maximum-number-of-words-found-in-sentences/)

# 2. 코드
### 1) Python
```python
class Solution:
    def mostWordsFound(self, sentences: List[str]) -> int:
        res = 0

        for s in sentences:
            res = max(res, len(s.split(" ")))

        return res
```

### 2) Java
```java
class Solution {
    public int mostWordsFound(String[] sentences) {
        int res = 0;
        
        for(String s: sentences) {
            res = Math.max(res, s.split(" ").length);
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const mostWordsFound = (sentences) => {
    let res = 0

    sentences.forEach(x => res = Math.max(res, x.split(" ").length))

    return res
};
```