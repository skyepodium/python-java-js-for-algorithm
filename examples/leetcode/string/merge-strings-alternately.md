# 1. 설명
- 두개의 문자열을 교차한 결과를 반환하세요


[문제 링크](https://leetcode.com/problems/merge-strings-alternately/)


# 2. 코드
### 1) Python
```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        
        return "".join([f"{a}{b}" for a, b in zip_longest(word1, word2, fillvalue="")])
```

### 2) Java
```java
class Solution {
    public String mergeAlternately(String word1, String word2) {

        // 1. init
        int n = Math.max(word1.length(), word2.length());
        StringBuilder res = new StringBuilder();

        // 2. loop
        for(int i=0; i<n; i++) {
            String w1 = i < word1.length() ? word1.charAt(i)+"" : "";
            String w2 = i < word2.length() ? word2.charAt(i)+"" : "";
            res.append(w1);
            res.append(w2);
        }

        return res.toString();
    }
}
```

### 3) JavaScript
```js
const mergeAlternately = (word1, word2) => {
    function* longestZip(a, b, fillValue) {
        const n = Math.max(a.length, b.length)

        for (let i = 0; i < n; i++) {
            const aVal = i < a.length ? a[i] : fillValue
            const bVal = i < b.length ? b[i] : fillValue
            yield `${aVal}${bVal}`
        }
    }

    return [...longestZip(word1, word2, "")].join("")
}
```