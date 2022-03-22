# 1. 설명
- 문자 2개를 바꿨을때 두개의 문자열이 동일한지를 반환하세요.


[문제 링크](https://leetcode.com/problems/check-if-one-string-swap-can-make-strings-equal/)


# 2. 코드
### 1) python
```python
class Solution:
    def areAlmostEqual(self, s1: str, s2: str) -> bool:
        # 0. exception
        if s1 == s2: return True

        # 1. init
        cnt = 0
        t = []

        # 2. loop
        for a, b in zip(s1, s2):
            if a != b:
                cnt += 1
                t.append((a, b))

            if cnt >= 3: return False

        return len(t) == 2 and t[0] == t[1][::-1]
```

### 2) java
```java
class Solution {
    public boolean areAlmostEqual(String s1, String s2) {
        // 0. exception
        if(s1.equals(s2)) return true;
        Map<Character, Character> m = new HashMap<>();

        int n = s1.length();
        int cnt = 0;
        Character lastKey = null;

        for(int i=0; i<n; i++) {
            char c1 = s1.charAt(i);
            char c2 = s2.charAt(i);

            if(c1 != c2) {
                cnt++;
                m.put(c1, c2);
                lastKey = c1;
            }

            if(cnt >= 3) return false;
        }
        return m.entrySet().size() == 2 && m.get(m.get(lastKey)) == lastKey;
    }
}
```

### 3) JavaScript
```js
const areAlmostEqual = (s1, s2) => {
    // 1. init
    if(s1 === s2) return true

    const n = s1.length
    const base = []
    let cnt = 0

    // 2. loop
    for(let i=0; i<n; i++) {
        const c1 = s1[i]
        const c2 = s2[i]

        if(c1 !== c2) {
            cnt++
            base.push([c1, c2])
        }

        if(cnt >= 3) return false
    }
    
    return base.length === 2 && base[0][0] === base[1][1] && base[0][1] === base[1][0]
};
```