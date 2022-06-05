# 1. 설명
- 제일 긴 nice string을 반환하세요


[문제 링크](https://leetcode.com/problems/longest-nice-substring/)


# 2. 코드
### 1) Python
```python
class Solution:
    def longestNiceSubstring(self, s: str) -> str:
        # 1. init
        n = len(s)
        res = ""

        # 2. loop
        for i in range(n):
            for j in range(i+1, n+1):
                # 1) set
                cur = s[i:j]
                se = set(cur)
                is_nice = True

                # 2) check
                for c in list(se):
                    if (c == c.lower() and c.upper() not in se) or (c == c.upper() and c.lower() not in se):
                        is_nice = False
                        break

                if is_nice and len(res) < len(cur):
                    print(cur)
                    res = cur

        return res
```

### 2) Java
```java
import java.util.HashSet;
import java.util.Set;

class Solution {
    public String longestNiceSubstring(String s) {
        // 1. init
        int n = s.length();
        String res = "";

        // 2. loop
        for(int i=0; i<n; i++) {
            for(int j=i+1; j<n+1; j++) {
                // 1) set
                boolean isNice = true;
                String cur = s.substring(i, j);
                Set<Character> se = new HashSet<>();
                for(int k=0; k<cur.length(); k++) {
                    char c = cur.charAt(k);
                    se.add(c);
                }

                for(int k=0; k<cur.length(); k++) {
                    char c = cur.charAt(k);
                    if(((int)c >= (int)'a' && !se.contains((char)(c - 32)))
                    || ((int)c < (int)'a' && !se.contains((char)(c + 32)))) {
                        isNice = false;
                        break;
                    }
                }

                if(isNice && res.length() < cur.length()) res = cur;
            }
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const longestNiceSubstring = (s) => {
    // 1. init
    const n = s.length
    let res = ""

    // 2. loop
    for(let i=0; i<n; i++) {
        for(let j=i+1; j<n+1; j++) {
            // set
            const cur = s.substring(i, j)
            const se = new Set(cur)
            let isNice = true
            for(const c of se.keys()) {
                if((c.charCodeAt(0) < "a".charCodeAt(0) && !se.has(c.toLowerCase()))
                || (c.charCodeAt(0) >= "a".charCodeAt(0) && !se.has(c.toUpperCase()))) {
                    isNice = false
                    break
                }
            }

            if(isNice && res.length < cur.length) res = cur
        }
    }

    return res
};

s = "YazaAay"
// s = "Bb"
// s = "c"

const res = longestNiceSubstring(s)

console.log('res', res)

```

### 4) TypeScript
```ts
const longestNiceSubstring = (s: string): string => {
    // 1. init
    const n:number = s.length
    let res:string = ""

    // 2. loop
    for(let i=0; i<n; i++) {
        for(let j=i+1; j<n+1; j++) {
            // set
            const cur:string = s.substring(i, j)
            const se:Set<string> = new Set(cur)
            let isNice:boolean = true

            for(const c of se.keys()) {
                if((c.charCodeAt(0) < "a".charCodeAt(0) && !se.has(c.toLowerCase()))
                    || (c.charCodeAt(0) >= "a".charCodeAt(0) && !se.has(c.toUpperCase()))) {
                    isNice = false
                    break
                }
            }

            if(isNice && res.length < cur.length) res = cur
        }
    }

    return res
};
```