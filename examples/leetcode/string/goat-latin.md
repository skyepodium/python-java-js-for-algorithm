# 1. 설명
- 규칙에 따라 문자열을 변경하세요

[문제 링크](https://leetcode.com/problems/goat-latin/)


# 2. 코드
### 1) Python
```python
class Solution:
    def toGoatLatin(self, sentence: str) -> str:
        # 1. init
        vowel = ['a', 'e', 'i', 'o', 'u']
        v = set(vowel)
        s = sentence.split(" ")
        n = len(s)

        # 2. loop
        for i in range(n):
            cur = s[i]
            if cur[0].lower() in v:
                s[i] += "ma"
            else:
                s[i] = s[i][1:] + s[i][0] + "ma"
            s[i] += "a" * (i+1)

        return " ".join(s)
```

### 2) Java
```java
import java.util.HashSet;
import java.util.Set;

class Solution {
    public String toGoatLatin(String sentence) {
        // 1. init
        Set<String> v = new HashSet<>();
        v.add("a");
        v.add("e");
        v.add("i");
        v.add("o");
        v.add("u");
        String[] s = sentence.split(" ");
        int n = s.length;

        // 2. loop
        for(int i=0; i<n; i++) {
            String cur = s[i];
            if(v.contains((cur.charAt(0) + "").toLowerCase())) {
                s[i] += "ma";
            }
            else {
                s[i] = s[i].substring(1) + s[i].charAt(0) + "ma";
            }
            for(int j=0; j<i+1; j++) s[i] += "a";
        }

        return String.join(" ", s);
    }
}
```

### 3) JavaScript
```js
const toGoatLatin = (sentence) => {
    // 1. init
    const s = sentence.split(" ")
    const n = s.length
    const vowel = ['a', 'e', 'i', 'o', 'u']
    const v = new Set(vowel)

    // 2. loop
    for(let i=0; i<n; i++) {
        let cur = s[i]

        if(v.has(cur[0].toLowerCase())) {
            s[i] += "ma"
        }
        else {
            s[i] = s[i].slice(1, ) + s[i][0] + "ma"
        }

        for(let j=0; j<i+1; j++) s[i] += "a"
    }

    return s.join(" ")
};
```