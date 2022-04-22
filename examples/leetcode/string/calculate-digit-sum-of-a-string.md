# 1. 설명
- 문자열에 포함된 숫자의 합을 구하세요


[문제 링크](https://leetcode.com/problems/calculate-digit-sum-of-a-string/)


# 2. 코드
### 1) python
```python
class Solution:
    def digitSum(self, s: str, k: int) -> str:

        def sum_str(st):
            res = 0
            for c in st:
                res += int(c)
            return str(res)

        while len(s) > k:
            base = ""
            for i in range(0, len(s), k):
                c = s[i:i+k]
                base += sum_str(c)
            s = base

        return s
```

### 2) java
```java
class Solution {
    public String digitSum(String s, int k) {
        while(s.length() > k) {
            String base = "";

            for(int i=0; i<s.length(); i+=k) {
                base += sumStr(s.substring(i, Math.min(i+k, s.length())));
            }

            s = base;
        }

        return s;
    }

    public String sumStr(String s) {
        int res = 0;

        for(int i=0; i<s.length(); i++) {
            char c = s.charAt(i);
            res += (int)c - (int)'0';
        }

        return Integer.toString(res);
    }
}
```

### 3) JavaScript
```js
const digitSum = (s, k) => {
    const sumStr = s => {
        let res = 0

        for(let i=0; i<s.length; i++) {
            const cur = s[i]
            res += cur.charCodeAt(0) - '0'.charCodeAt(0)
        }

        return String(res)
    }

    while(s.length > k) {
        let base = ""

        for(let i=0; i<s.length; i+=k) {
            base += sumStr(s.substring(i, i+k))
        }

        s = base
    }

    return s
};
```