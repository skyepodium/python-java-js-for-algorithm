# 1. 설명
- 올바른 라이센스키를 반환하세요


[문제 링크](https://leetcode.com/problems/license-key-formatting/)


# 2. 코드
### 1) python
```python
class Solution:
    def licenseKeyFormatting(self, s: str, k: int) -> str:
        s = s.replace("-", "")[::-1].upper()
        n = len(s)

        t = ""
        for i in range(0, n, k):
            t += s[i:i+k] + "-"

        t = t[0:len(t) - 1]

        return t[::-1]
```

### 2) java
```java
class Solution {
    public String licenseKeyFormatting(String s, int k) {
        s = new StringBuilder(s.replaceAll("-", "").toUpperCase()).reverse().toString();
        int n = s.length();

        StringBuilder t = new StringBuilder();
        for(int i=0; i<n; i+=k) {
            t.append(s.substring(i, Math.min(i+k, n)));
            if(i+k<n) t.append("-");
        }

        return t.reverse().toString();
    }
}
```

### 3) JavaScript
```js
const licenseKeyFormatting = (s, k) => {

    s = s.replace(/-/g, "").split("").reverse().join("").toUpperCase()
    const n = s.length

    let t = ""
    for(let i=0; i<n; i+=k) {
        t += s.slice(i, i+k) + "-"
    }

    t = t.slice(0, t.length - 1)

    return t.split("").reverse().join("")
};
```