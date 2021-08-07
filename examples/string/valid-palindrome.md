# 1. 설명
- 주어진 문자열이 팰림드롬인지 확인한다.
- 대소문자 구분하지 않는다.
- 영문자와 숫자를 대상으로 한다.

문자열의 길이 1 <= n <= 20만


[문제 링크](https://leetcode.com/problems/valid-palindrome/)


# 2. 코드
### 1) python
```python
import re

class Solution:
    def isPalindrome(self, s: str) -> bool:
        # 1. 정규표현식으로 영문자, 숫자이외의 문자 제거, 
        # 2. 모두 소문자로 변환
        s = re.sub('[^a-z0-9]', '', s.lower())
        
        # 3. 슬라이싱으로 문자열 뒤집고 같은지 확인
        return s == s[::-1]
```

### 2) java
문자열의 길이가 20만이고 O(n)으로 비교해도 된다고 생각했기 때문에 StringBuffer 클래스 사용

속도가 중요하다면 투포인터 사용
```java
class Solution {
    public boolean isPalindrome(String s) {
        // 1. 정규표현식으로 영문자, 숫자이외의 문자 제거, 
        // 2. 모두 소문자로 변환
        s = s.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();
        
        // 3. StringBuffer 클래스를 사용해서 문자열 뒤집기
        StringBuffer sb = new StringBuffer(s);
        String reversed = sb.reverse().toString();
        
        // 4. 두 문자열의 값이 같은지 equals로 확인
        return s.equals(reversed);
    }
}
```