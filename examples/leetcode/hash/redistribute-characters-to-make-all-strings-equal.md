# 1. 설명
- 모두 같은 문자열을 만들 수 있는지 여부를 반환하세요

[문제 링크](https://leetcode.com/problems/redistribute-characters-to-make-all-strings-equal/)

# 2. 코드
### 1) Python
```python
class Solution:
    def makeEqual(self, words: List[str]) -> bool:
        # 1. init
        n = len(words)

        # 2. loop
        for val in Counter("".join(words)).values():
            if val % n != 0: return False

        return True
```

### 2) Java
```java
class Solution {
    public boolean makeEqual(String[] words) {
        // 1. init
        int n = words.length;
        Map<Character, Integer> m = new HashMap<>();

        // 2. count
        Arrays.stream(words).forEach(x -> {
            for(int i=0; i<x.length(); i++) {
                char cur = x.charAt(i);
                m.put(cur, m.getOrDefault(cur, 0) + 1);
            }
        });

        // 3. loop
        for(int c: m.values()) {
            if(c % n != 0) return false;
        }

        return true;
    }
}
```

### 3) JavaScript
```js
const makeEqual = (words) => {
    // 1. init
    const n = words.length
    const m = new Map()

    // 2. loop
    words.forEach(x => {
        for(let i=0; i<x.length; i++) {
            const cur = x[i]
            if(m.has(cur)) m.set(cur, m.get(cur) + 1)
            else m.set(cur, 1)
        }
    })

    // 3. search
    for(const c of m.values()) {
        if(c % n !== 0) return false
    }

    return true
};
```