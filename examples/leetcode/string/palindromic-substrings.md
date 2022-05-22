# 1. 설명
- 팰린드롬의 개수를 구하세요


[문제 링크](https://leetcode.com/problems/palindromic-substrings/)

# 참고
파이썬 알고리즘 인터뷰 책을 읽었던 것이 도움이 되었다.

# 2. 코드
### 1) Python
```python
class Solution:
    def countSubstrings(self, s: str) -> int:
        # 1. init
        n = len(s)
        self.res = 0

        # 2. is_palindrome
        def is_palindrome(l, r):
            while 0 <= l and r < n and s[l] == s[r]:
                self.res += 1
                l -= 1
                r += 1

        # 3. loop
        for i in range(n):
            is_palindrome(i, i)
            is_palindrome(i, i+1)

        return self.res
```

### 2) Java
```java
class Solution {
    public int countSubstrings(String s) {
        // 1. init
        int n = s.length();
        int res = 0;

        // 2. loop
        for(int i=0; i<n; i++) {
            res += isPalindrome(i, i, n, s);
            res += isPalindrome(i, i+1, n, s);
        }

        return res;
    }

    public int isPalindrome(int l, int r, int n, String s) {
        int res = 0;

        while(l >= 0 && r < n && s.charAt(l) == s.charAt(r)) {
            res++;
            l--;
            r++;
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const countSubstrings = (s) => {
    // 1. init
    const n = s.length
    let res = 0

    // 2. isPalindrome
    const isPalindrome = (l, r) => {
        while(l >= 0 && r < n && s[l] === s[r]) {
            res++
            l--
            r++
        }
    }

    // 3. loop
    for(let i=0; i<n; i++) {
        isPalindrome(i, i)
        isPalindrome(i, i+1)
    }

    return res
};
```

### 4) TypeScript
```ts
const countSubstrings = (s: string): number => {
    // 1. init
    const n:number = s.length
    let res:number = 0

    // 2. isPalindrome
    const isPalindrome = (l:number, r:number) => {
        while(l >= 0 && r < n && s[l] === s[r]) {
            res++
            l--
            r++
        }
    }

    // 3. loop
    for(let i=0; i<n; i++) {
        isPalindrome(i, i)
        isPalindrome(i, i+1)
    }

    return res
};
```