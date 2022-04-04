# 1. 설명
- 숫자가 포함된 문자열을 복호화하세요

[문제 링크](https://leetcode.com/problems/decrypt-string-from-alphabet-to-integer-mapping/)


# 2. 코드
### 1) Python
```python
class Solution:
    def freqAlphabets(self, s: str) -> str:

        def get_alphabet(n):
            return f"{chr(ord('a') + n - 1)}"

        for num in range(26, -1, -1):
            pattern = f"{num}#" if num >= 10 else f"{num}"
            s = re.sub(pattern, get_alphabet(num), s)

        return s
```

### 2) Java
```java
class Solution {
    public String freqAlphabets(String s) {

        for(int i=26; i>=0; i--) {
            String pattern = i >= 10 ? i + "#" : i + "";
            s = s.replaceAll(pattern, getAlphabet(i));
        }

        return s;
    }

    public String getAlphabet(int n) {
        return (char)((int)'a' + n - 1) + "";
    }
}
```

### 3) JavaScript
```js
const freqAlphabets = (s) => {
    const getAlphatbet = (n) => {
        return String.fromCharCode("a".charCodeAt(0) + n - 1)
    }

    for(let i=26; i>=0; i--) {
        const pattern = i >= 10 ? `${i}#` : `${i}`
        const regex = new RegExp(pattern, 'g')
        s = s.replace(regex, getAlphatbet(i))
    }

    return s
};
```