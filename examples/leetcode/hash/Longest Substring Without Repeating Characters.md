# 1. 설명
- 문자열 S의 부분 문자열중 중복이 없는 경우의 최대길이를 반환하세요.


[문제 링크](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

# 2. 코드
### 1) python
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        # 1. init
        d = {}
        l = 0
        res = 0

        # 2. loop
        for r, cur in enumerate(s):
            # 1) dup check
            if cur in d:
                l = max(l, d[cur] + 1)

            # 2) insert
            d[cur] = r

            # 3) update
            res = max(res, r-l+1)

        return res
```

### 2) java
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        // 1. init
        Map<Character, Integer> m = new HashMap<>();
        int n = s.length();
        int res = 0;
        int l = 0;

        // 2. loop
        for(int r=0; r<n; r++) {
            char c = s.charAt(r);

            if(m.containsKey(c)) {
                l = Math.max(l, m.get(c) + 1);
            }

            m.put(c, r);

            res = Math.max(res, r - l + 1);
        }

        return res;
    }
}
```

### 3) JavaScript
```js
var lengthOfLongestSubstring = function(s) {
    // 1. init
    let res = 0
    let l = 0
    let maxLength = 0
    const m = new Map()

    // 2. loop
    s.split("").forEach((x, r) => {
        // 1) dup check
        if(m.has(x)) {
            l = Math.max(l, m.get(x) + 1)
        }

        // 2) insert
        m.set(x, r)

        // 3) update
        maxLength = Math.max(maxLength, r-l+1)
    })

    return maxLength
};
```