# 1. 설명
- 도착지점을 구하세요

[문제 링크](https://leetcode.com/problems/destination-city/)

# 2. 코드
### 1) python
```python
class Solution:
    def destCity(self, paths: List[List[str]]) -> str:
        # 1. init
        d = defaultdict(str)

        # 2. make graph
        for s, e in paths:
            d[s] = e

        # 3. search
        node = paths[0][0]
        while d[node]:
            node = d[node]

        return node
```

### 2) Java
```java
class Solution {
    public String destCity(List<List<String>> paths) {
        // 1. init
        Map<String, String> m = new HashMap<>();

        // 2. make graph
        paths.forEach(x -> m.put(x.get(0), x.get(1)));

        String node = paths.get(0).get(0);
        while(m.get(node) != null) {
            node = m.get(node);
        }

        return node;
    }
}
```

### 3) JavaScript
```js
const destCity = (paths) => {
    // 1. init
    const m = new Map()

    // 2. make graph
    paths.forEach(x => m.set(x[0], x[1]))

    // 3. search
    let node = paths[0][0]
    while(true) {
        node = m.get(node)
        if(!m.has(node)) break
    }

    return node
};
```