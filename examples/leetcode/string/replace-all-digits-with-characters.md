# 1. 설명
- 규칙에 따라 숫자를 문자로 변경하세요.


[문제 링크](https://leetcode.com/problems/replace-all-digits-with-characters/)


# 2. 코드
### 1) Python
```python
class Solution:
    def replaceDigits(self, s: str) -> str:
        # 1. init
        characters = [x for x in re.split("[0-9]+", s) if x != '']
        nums = [x for x in re.split("[a-z]", s) if x != '']
        diff = abs(len(characters) - len(nums))
        res = []

        # 2. loop
        for c, n in zip(characters, nums):
            n_ord = (ord(c) - ord('a') + int(n)) % 26 + ord('a')
            res.append(chr(n_ord))

        return "".join([f"{a}{b}" for a, b in zip(characters, res)]) + "".join(characters[len(characters) - diff:])
```

### 2) Java
```java

```

### 3) JavaScript
```js
```