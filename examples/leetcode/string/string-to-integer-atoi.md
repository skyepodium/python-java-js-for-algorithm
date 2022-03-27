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
import java.util.regex.Matcher;
import java.util.regex.Pattern;

class Solution {
    public int myAtoi(String s) {
        // step 1
        Pattern pattern = Pattern.compile("^ +[0-9]+");
        Matcher matcher = pattern.matcher(s);
        if(matcher.find()) {
            return check(matcher.group().trim());
        }

        // step 2
        pattern = Pattern.compile("^ *[-+][0-9]+");
        matcher = pattern.matcher(s);
        if(matcher.find()) {
            return check(matcher.group().trim());
        }

        // step 3
        pattern = Pattern.compile("^[0-9]+ *");
        matcher = pattern.matcher(s);
        if(matcher.find()) {
            return check(matcher.group().trim());
        }


        return 0;
    }

    public int check(String strNum) {
        strNum = strNum.replaceAll("^[0]+", "");
        if(strNum.length() < 1) return 0;
        if(strNum.length() > 2 && strNum.charAt(0) == '-' && strNum.charAt(1) == '0') {
            strNum = "-" + strNum.replaceAll("^-[0]+", "");
        }

        if(strNum.length() > 2 && strNum.charAt(0) == '+' && strNum.charAt(1) == '0') {
            strNum = strNum.replaceAll("^+[0]+", "");
        }


        if(strNum.length() >= 12) {
            return strNum.charAt(0) == '-' ? Integer.MIN_VALUE : Integer.MAX_VALUE;
        }

        long num = Long.parseLong(strNum);
        if(num < Integer.MIN_VALUE) return Integer.MIN_VALUE;
        else if(num > Integer.MAX_VALUE) return Integer.MAX_VALUE;
        else return (int)num;
    }
}
```

### 3) JavaScript
```js
const myAtoi = (s) => {
    // 1. init
    const MIN_INT = -2147483648
    const MAX_INT = 2147483647

    // 2. check
    const check = (val) => {
        val = Number(val)
        if(val < MIN_INT) return MIN_INT
        else if(val > MAX_INT) return MAX_INT
        else return val
    }

    // step 1
    const a = s.match("^ +[0-9]+")
    if(a) return check(a[0].trim())

    // step 2
    const b = s.match("^ *[-+][0-9]+")
    if(b) return check(b[0].trim())

    // step 3
    const c = s.match("^[0-9]+ *")
    if(c) return check(c[0].trim())


    return 0
};
```