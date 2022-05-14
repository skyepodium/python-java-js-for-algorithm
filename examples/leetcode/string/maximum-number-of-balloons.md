# 1. 설명
- ballon의 개수를 구하세요

[문제 링크](https://leetcode.com/problems/maximum-number-of-balloons/)


# 2. 코드
### 1) Python
```python
from collections import Counter

class Solution:
    def maxNumberOfBalloons(self, text: str) -> int:
        c = Counter(text)

        return min(c['b'], c['a'], c['l']//2, c['o']//2, c['n'])
```

### 2) Java
```java
import java.util.Arrays;
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int maxNumberOfBalloons(String text) {
        // 1. init
        Map<String, Integer> m = new HashMap<>();
        Arrays.stream(text.split("")).forEach(c -> m.put(c, m.getOrDefault(c, 0) + 1));

        return min5(m.getOrDefault("b", 0), m.getOrDefault("a", 0), m.getOrDefault("l", 0) / 2, m.getOrDefault("o", 0) / 2, m.getOrDefault("n", 0));
    }

    public int min5(int a, int b, int c, int d, int e) {
        return Math.min(a, Math.min(b, Math.min(c, Math.min(d, e))));
    }
}
```

### 3) JavaScript
```js
const maxNumberOfBalloons = (text) => {
    // 1. init
    const m = new Map()

    // 2. count
    text.split("").forEach(c => {
        const cnt = m.has(c) ? m.get(c) + 1 : 1
        m.set(c, cnt)
    })

    // 3. res
    const res = Math.min(m.get('b'), m.get('a'), Math.trunc(m.get('l')/2), Math.trunc(m.get('o')/2), m.get('n'))

    return isNaN(res) ? 0 : res
};
```

### 4) TypeScript
```ts
const maxNumberOfBalloons = (text:string):number => {
    // 1. init
    const m = new Map<string, number>()

    // 2. count
    text.split("").forEach(c => {
        const cnt:number = m.has(c) ? m.get(c) + 1 : 1
        m.set(c, cnt)
    })

    // 3. res
    const res:number = Math.min(m.get('b'), m.get('a'), Math.trunc(m.get('l')/2), Math.trunc(m.get('o')/2), m.get('n'))

    return isNaN(res) ? 0 : res
};
```