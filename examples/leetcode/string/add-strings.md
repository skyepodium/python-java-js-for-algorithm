# 1. 설명
- 두개의 문자열 숫자를 더한 결과를 반환하세요.
- 문자를 숫자로 변경하는 Built-in 함수를 사용하지 마세요.


[문제 링크](https://leetcode.com/problems/add-strings/)


# 2. 코드
### 1) python
```python
class Solution:
    def addStrings(self, num1: str, num2: str) -> str:
        # 1. init
        n = len(num1) - 1
        m = len(num2) - 1

        # 2. loop
        carry = 0
        res = ""
        while n >= 0 or m >= 0 or carry > 0:
            a = 0
            if n >= 0:
                a = ord(num1[n]) - ord('0')
                n -= 1

            b = 0
            if m >= 0:
                b = ord(num2[m]) - ord('0')
                m -= 1

            carry, val = divmod(a + b + carry, 10)
            res += str(val)

        # 3. reverse
        return res[::-1]
```

### 2) java
```java
class Solution {
    public String addStrings(String num1, String num2) {
        // 1. init
        int n = num1.length() - 1;
        int m = num2.length() - 1;

        char[] num1Array = num1.toCharArray();
        char[] num2Array = num2.toCharArray();

        // 2. loop
        int carry = 0;
        String res = "";
        while(n >= 0 || m >= 0 || carry > 0) {
            int a = n >= 0 ? num1Array[n--] - '0' : 0;
            int b = m >= 0 ? num2Array[m--] - '0' : 0;

            int sumVal = a + b + carry;
            carry = sumVal / 10;
            int val = sumVal % 10;
            res += Integer.toString(val);
        }

        // 3. reverse
        StringBuffer sb = new StringBuffer(res);
        return sb.reverse().toString();
    }
}
```