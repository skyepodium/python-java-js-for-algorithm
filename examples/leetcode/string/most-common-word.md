# 1. 설명
- 영문자만 대상으로 한다.
- 대소문자 구분하지 않는다.
- 금지된 단어는 제외한다.
- 가장 많이 언급된 단어를 반환하세요.

- 문자열의 길이 1 <= n <= 1000


[문제 링크](https://leetcode.com/problems/most-common-word/)


# 2. 코드
### 1) Python
```python
class Solution:
    def mostCommonWord(self, paragraph: str, banned: List[str]) -> str:

        return Counter([w for w in re.sub("[^a-zA-Z]", " ", paragraph).lower().split() if w not in set(banned)]).most_common(1)[0][0]
```

### 2) Java
- set - 금지된 단어 저장
- map - 단어별 개수 저장
```java
import java.util.*;
import java.util.stream.Collectors;

class Solution {
    public String mostCommonWord(String paragraph, String[] banned) {
        // 1. init
        Set<String> s = Arrays.stream(banned).collect(Collectors.toSet());
        String[] p = paragraph.toLowerCase().replaceAll("[^a-z]", " ").split(" +");
        Map<String, Integer> m = new HashMap<>();

        // 2. count
        for(String a: p) {
            if(s.contains(a)) continue;
            m.put(a, m.getOrDefault(a, 0) + 1);
        }

        return m.entrySet().stream()
                    .sorted((a, b) -> b.getValue() - a.getValue())
                    .collect(Collectors.toList())
                    .get(0)
                    .getKey();
    }
}
```

### 3) JavaScript
```js
const mostCommonWord = (paragraph, banned) => {
    // 1. init
    const s = new Set(banned)
    const p = paragraph.toLowerCase()
            .replace(/[^a-zA-Z]/g, ' ')
            .split(/ +/)
            .filter(x => x !== '')
    const m = new Map()

    // 2. loop
    p.forEach(w => {
        if(!s.has(w)) {
            if(m.has(w)) m.set(w, m.get(w) + 1)
            else m.set(w, 0)
        }
    })

    return [...m.entries()].sort((a, b) => b[1] - a[1])[0][0]
};
```