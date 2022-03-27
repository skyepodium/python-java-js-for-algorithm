# 1. 설명
- 규칙에 따라 문자열을 정수로 변환하세요


[문제 링크](https://leetcode.com/problems/string-to-integer-atoi/)


# 2. 코드
### 1) python
```python
class Solution:
    def myAtoi(self, s: str) -> int:
        # 1. init
        MIN_INT = -2147483648
        MAX_INT = 2147483647

        # 2. def
        def check(val):
            res = int(val.strip())
            if res < MIN_INT: res = MIN_INT
            elif res > MAX_INT: res = MAX_INT
            return res

        # step 1
        a = re.findall("^ +[0-9]+", s)
        if a:
            return check(a[0])

        # step 2
        b = re.findall("^ *[-+][0-9]+", s)
        if b:
            return check(b[0])

        # step 3
        c = re.findall("^[0-9]+ *", s)
        if c:
            return check(c[0])

        return 0
```

### 2) java
```java

```

### 3) JavaScript
```js

```