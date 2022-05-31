# 1. 설명
- 문자열의 부분문자열이 0 ~ 1 << k 를 모두 포함하는지 여부를 반환하세요

[문제 링크](https://leetcode.com/problems/check-if-a-string-contains-all-binary-codes-of-size-k/)

# 2. 코드
### 1) Python
```python
class Solution:
    def hasAllCodes(self, s: str, k: int) -> bool:
        # 1. init
        seen = set()
        n = len(s)
        cnt = 2 ** k

        # 2. loop
        for i in range(n - k + 1):
            cur = s[i:i+k]
            if cur not in seen:
                cnt -= 1
                seen.add(cur)
            if cnt == 0: return True

        return False
```

### 2) Java
```java
import java.util.HashSet;
import java.util.Set;

class Solution {
    public boolean hasAllCodes(String s, int k) {
        // 1. init
        int n = s.length();
        int cnt = 1 << k;
        Set<String> seen = new HashSet<>();

        // 2. loop
        for(int i=0; i<n-k+1; i++) {
            String cur = s.substring(i, i+k);
            if(!seen.contains(cur)) {
                cnt--;
                seen.add(cur);
            }
            if(cnt == 0) return true;
        }
        
        return false;
    }
}
```

### 3) JavaScript
```js
const hasAllCodes = (s, k) => {
    // 1. init
    const seen = new Set()
    const n = s.length
    let cnt = 1 << k

    // 2. loop
    for(let i=0; i<n-k+1; i++) {
        const cur = s.substring(i, i+k)
        if(!seen.has(cur)) {
            cnt--
            seen.add(cur)
        }
        if(cnt === 0) return true
    }

    return false
};
```

### 4) TypeScript
```ts
const hasAllCodes = (s: string, k: number): boolean => {
    // 1. init
    const seen = new Set<string>()
    const n:number = s.length
    let cnt:number = 1 << k

    // 2. loop
    for(let i=0; i<n-k+1; i++) {
        const cur:string = s.substring(i, i+k)
        if(!seen.has(cur)) {
            cnt--
            seen.add(cur)
        }
        if(cnt === 0) return true
    }

    return false
};
```