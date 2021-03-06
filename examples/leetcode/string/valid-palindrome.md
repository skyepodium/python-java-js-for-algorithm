# 1. 설명
- 주어진 문자열이 팰림드롬인지 확인한다.
- 대소문자 구분하지 않는다.
- 영문자와 숫자를 대상으로 한다.

- 문자열의 길이 1 <= n <= 20만


[문제 링크](https://leetcode.com/problems/valid-palindrome/)


# 2. 코드
### 1) python
```python
'''
시간 복잡도: O(N)
공간 복잡도: O(1)
사용한 알고리즘: 정규 표현식, 슬라이싱
사용한 자료구조: -
'''
import re

class Solution:
    def isPalindrome(self, s: str) -> bool:
        # 1. 정규표현식으로 영문자, 숫자이외의 문자 제거
        # 2. 모두 소문자로 변환
        s = re.sub('[^a-z0-9]', '', s.lower())
        
        # 3. 슬라이싱으로 문자열 뒤집고 같은지 확인
        return s == s[::-1]
```

### 2) java
정규 표현식, 투포인터 사용
```java
/*
    시간 복잡도: O(N) - N 문자열의 길이, 소문자 변환을 위해 문자열 전체 순회
    공간 복잡도: O(1) - 새로운 자료구조 사용 X
    사용한 알고리즘: 정규표현식, 투 포인터
    사용한 자료구조: -
 */

class Solution {
    public boolean isPalindrome(String s) {
        // 1. 정규 표현식
        // 소문자 변환, 소문자-숫자 이외 모두 제거
        s = s.toLowerCase().replaceAll("[^a-z0-9]", "");

        // 2. 투포인터
        // 최대 문자열 길이의 절반만큼 반복
        int l = 0;
        int r = s.length() - 1;
        while(l < r) {
            if(s.charAt(l) != s.charAt(r)) return false;
            l++;
            r--;
        }

        return true;
    }
}
```

### 3) JavaScript
```js
const isPalindrome = s => {
    // 1. 소문자 변경
    s = s.toLowerCase()

    // 2. replace 메서드, 정규식 치환
    s = s.replace(/[^a-z0-9]/g, "")

    // 3. 문자열 뒤집기
    return s === s.split("").reverse().join("")
};
```

### 4) TypeScript
```ts
const isPalindrome = (s: string): boolean => {
    s = s.toLowerCase().replace(/[^a-z\d]/g, '')

    return s === s.split("").reverse().join("")
};
```

### 5) Kotlin
```kt
class Solution {
    fun isPalindrome(s: String): Boolean {
        val t = s.toLowerCase().replace("[^a-zA-Z0-9]".toRegex(), "")
        println(t)
        return t == t.reversed();
    }
}
```

### 6) C++
```cpp
#include <iostream>
#include <string>
#include <vector>

using namespace std;

class Solution {
public:
    bool isPalindrome(string s) {
        // 1. init
        s = toLower(s);
        
        // 2. two pointer
        int n = (int)s.size();
        int l = 0;
        int r = n - 1;
        
        while(l < r) {
            while(l < n && !isAlNum(s[l])) l++;
            while(r >= 0 && !isAlNum(s[r])) r--;
            
            if(l >= r) break;
            if(l >= s.size() || r < 0) break;

            
            if(s[l] != s[r]) return false;
            l++;
            r--;
        }
        
        return true;
    }
    
    string toLower(string s) {
        string res = "";
        
        for(int i=0; i<s.size(); i++) {
            char c = s[i];
            if(c >= 'A' && c <= 'Z') c += 32;
            res += c;
        }
        
        return res;
    }
    
    bool isAlNum(char c) {
        return (48 <= c && c <= 57) || (65 <= c && c <= 90) || (97 <= c && c <= 122);
    }
};
```