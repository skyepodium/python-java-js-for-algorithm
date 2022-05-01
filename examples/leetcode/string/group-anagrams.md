# 1. 설명
- 반환 순서는 상관없다.
- anagram별로 그룹화 해서 반환하세요

- 배열의 길이 1 <= n <= 10만
- 문자열의 길이 1 <= m <= 100


[문제 링크](https://leetcode.com/problems/group-anagrams/)


# 2. 코드
### 1) python
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        # 1. init
        d = defaultdict(list)

        # 2. loop
        for idx, s in enumerate(strs):
            d["".join(sorted(s))].append(s)

        return d.values()
```

### 2) Java
```java
import java.util.*;

class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        // 1. init
        Map<String, List<String>> m = new HashMap<>();

        // 2. loop
        for(String s: strs) {
            char[] c = s.toCharArray();
            Arrays.sort(c);
            String key = new String(c);

            List<String> t = m.getOrDefault(key, new ArrayList<>());
            t.add(s);
            m.put(key, t);
        }

        return new ArrayList<>(m.values());
    }
}
```

### 3. JavaScript
```js
var groupAnagrams = function(strs) {
    // 1. init
    const m = new Map()

    // 2. loop
    strs.forEach(s => {
        const key = s.split("")
            .sort((a, b) => a.localeCompare(b))
            .join("")
        m.has(key) ? m.set(key, m.get(key).concat([s])) : m.set(key, [s])
    })

    return [...m.values()]
};
```