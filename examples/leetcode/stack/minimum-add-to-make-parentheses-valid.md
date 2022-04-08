# 1. 설명
- 올바른 괄호를 만드는데 필요한 괄호의 개수를 구하세요


[문제 링크](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/)


# 2. 코드
### 1) Python
```python
class Solution:
    def minAddToMakeValid(self, s: str) -> int:
        # 1. init
        cnt = 0
        need = 0

        # 2. loop
        for c in s:
            if c == '(':
                cnt += 1
            else:
                if cnt > 0 :
                    cnt -= 1
                else:
                    need += 1
                    continue
                    
        return need + cnt
```

### 2) Java
```java
class Solution {
    public int minAddToMakeValid(String s) {
        // 1. init
        int cnt = 0;
        int need = 0;

        // 2. loop
        for(int i=0; i<s.length(); i++) {
            char cur = s.charAt(i);
            if(cur == '(') cnt++;
            else {
                if(cnt > 0) cnt--;
                else need++;
            }
        }

        return cnt + need;
    }
}
```

### 3) JavaScript
```js
const minAddToMakeValid = (s) => {
    // 1. init
    let cnt = 0
    let need = 0

    // 2. loop
    s.split("").forEach(x => {
        if(x === '(') cnt++
        else {
            if(cnt > 0) cnt--
            else need++
        }
    })

    return cnt + need
};
```

### 4) Kotlin
```kt
class Solution {
    fun minAddToMakeValid(s: String): Int {
        // 1. loop
        var cnt = 0
        var need = 0

        // 2. loop
        for(i in 0..s.length-1) {
            if(s[i] == '(') cnt++
            else {
                if(cnt > 0) cnt--
                else need++
            }
        }

        return cnt + need
    }
}
```

### 5) TypeScript
```ts
const minAddToMakeValid = (s: string): number => {
    // 1. init
    let cnt = 0
    let need = 0
    
    // 2. loop
    s.split("").forEach(x => {
        if(x === '(') cnt++
        else {
            if(cnt > 0) cnt--
            else need++
        }
    })
    
    return cnt + need
};
```