# 1. 설명
- 가장 긴 팰린드롬 부분 문자열을 반환하세요.

- 문자열의 길이 1 <= n <= 1000



[문제 링크](https://leetcode.com/problems/longest-palindromic-substring/)

# 2. 코드
### 1) python
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:

        result = ""

        # 1. 예외 처리
        if len(s) < 2 or s == s[::-1]:
            return s

        # 2. 투 포인터
        def expand(l, r):
            while l >= 0 and r <= len(s) and s[l] == s[r-1]:
                l -= 1
                r += 1

            # 현재 투포인터가 있는 위치가 팰린드롬이 아니거나
            # 인덱스를 넘어갔기 때문에 바로 이전 상태로 돌아간다.
            # 처음부터 팰린드롬이 아닌경우, 홀수개는 문자 1개, 짝수개는 빈문자열을 반환한다.
            return s[l+1: r-1]

        # 3. 한개씩 중심 탐색
        for i in range(len(s) - 1):
            result = max(result,
                         expand(i, i+1),
                         expand(i, i+2),
                         key=len
                         )

        return result
```

### 2) java
```java
class Solution {
    public String longestPalindrome(String s) {

        String result = "";
        int size = s.length();

        // 1. 에외 처리
        if(size < 2 || s.equals(reverString(s))) return s;

        // 2. 중심점 하나씩 탐색
        for(int i=0; i<=size-1; i++) {
            result = maxString3(result,
                    // 3. 투 포인터 확장
                    expand(i, i+1, s),
                    expand(i, i+2, s)
            );
        }

        return result;
    }

    public String expand(int l, int r, String s) {

        while (l >= 0 && r <= s.length() && s.charAt(l) == s.charAt(r-1)) {
            l--;
            r++;
        }
        return s.substring(l+1, r-1);
    }

    public String maxString(String a, String b) {
        return a.length() > b.length() ? a : b;
    }

    public String maxString3(String a, String b, String c) {
        return maxString(maxString(a, b), c);
    }

    public String reverString(String s) {
        StringBuilder sb = new StringBuilder(s);
        return sb.reverse().toString();
    }
}
```

### JavaScript
```js
var longestPalindrome = function(s) {
    // 0. exception
    if(s.length < 2 || s === s.split("").reverse().join("")) return s

    // 1. init
    let result = ""

    // 2. two pointer
    const expand  = (l, r) => {
        while(l >= 0 && r <= s.length && s[l] === s[r-1]) {
            l--
            r++
        }
        return s.slice(l+1, r-1)
    }

    const maxString = (a, b) => {
        return a.length < b.length ? b : a
    }

    const maxString3 = (a, b, c) => {
        return maxString(a, maxString(b, c))
    }

    // 3. search
    s.split("").forEach((_, i) => {
        result = maxString3(result
            ,   expand(i, i+1)
            ,   expand(i, i+2))
    })

    return result
};
```