# 1. 설명
- 주어진 숫자의 팰린드롬 여부를 반환하세요


[문제 링크](https://leetcode.com/problems/palindrome-number/)


# 2. 코드
### 1) Python
```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        s = str(x)
        
        return s == s[::-1]
```

### 2) Java
```java
class Solution {
    public boolean isPalindrome(int x) {
        String s = Integer.toString(x);

        return s.equals(new StringBuffer(s).reverse().toString());
    }
}
```

### 3) JavaScript
```js
const isPalindrome = (x) => {
    const s = String(x)

    return s === s.split("").reverse().join("")
};
```

### 4) TypeScript
```ts
const isPalindrome = (x: number): boolean => {
    const s: string = String(x)

    return s === s.split("").reverse().join("")
};
```

### 5) C++
```cpp
class Solution {
   public:
    bool isPalindrome(int x) {
        string s = to_string(x);

        int l = 0;
        int r = s.size() - 1;

        while (l < r) {
            if (s[l] != s[r]) {
                return false;
            }
            l++;
            r--;
        }
        return true;
    }
};
```