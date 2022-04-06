# 1. 설명
- 

[문제 링크](https://leetcode.com/problems/divide-a-string-into-groups-of-size-k/)


# 2. 코드
### 1) Python
```python
class Solution:
    def divideString(self, s: str, k: int, fill: str) -> List[str]:

        return [s[i:i+k] if i+k <= len(s) else s[i:i+k] + fill * (i+k - len(s)) for i in range(0, len(s), k)]
```

### 2) Java
```java
class Solution {
    public String[] divideString(String s, int k, char fill) {
        // 1. init
        List<String> res = new ArrayList<>();
        int n = s.length();
        int cnt = n % k != 0 ? n / k + 1 : n / k;

        StringBuilder base = new StringBuilder();
        for(int i=0; i<k; i++) base.append(fill);
        String b = base.toString();

        // 2. loop
        for(int i=0; i<n; i+=k) {
            res.add(s.substring(i, Math.min(i+k, n)));
        }

        // 3. map
        return res.stream().map(x -> x.length() < k ? x + b.substring(0, k - x.length()) : x)
                .collect(Collectors.toList())
                .toArray(new String[cnt]);
    }
}
```

### 3) JavaScript
```js
const divideString = (s, k, fill) => {

    const res = []
    for(let i=0; i<s.length; i += k) {
        res.push(s.substring(i, i+k))
    }

    return res.map(x => {
        return x.length < k ? x.padEnd(k, fill) : x
    })
};
```