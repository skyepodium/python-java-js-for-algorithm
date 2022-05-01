# 1. 설명
- `#`는 백스페이스 문자입니다. 문자를 지웠을 때 두 문자열 s,t 의 동일여부를 반환하세요

[문제 링크](https://leetcode.com/problems/backspace-string-compare/)

# 참고
처음에는 while문을 사용했었는데 이 문제는 스택을 사용하는 것이 맞다. 스택을 위한 문제다.

스택의 장점인 top을 O(1)만에 볼 수 있고, 거꾸로 지울 수 있다는 것을 항상 생각하자.


# 2. 코드
### 1) Python
```python
class Solution:
    def backspaceCompare(self, s: str, t: str) -> bool:

        def refine(a):
            st = []
            for c in a:
                if c != '#':
                    st.append(c)
                else:
                    if st: st.pop()
            return st

        return refine(s) == refine(t)
```

### 2) Java
```java
import java.util.Stack;

class Solution {
    public boolean backspaceCompare(String s, String t) {
        return refine(s).equals(refine(t));
    }

    public String refine(String s) {
        Stack<Character> st = new Stack<>();
        for(int i=0; i<s.length(); i++) {
            char cur = s.charAt(i);
            if(cur != '#') {
                st.add(cur);
            }
            else {
                if(!st.isEmpty()) st.pop();
            }
        }

        StringBuilder sb = new StringBuilder();
        while(!st.isEmpty()) {
            sb.append(st.pop());
        }
        return sb.toString();
    }
}
```

### 3) JavaScript
```js
const backspaceCompare = (s, t) => {

    const refine = (s) => {
        const st = []

        s.split("").forEach(x => {
            if(x !== '#') {
                st.push(x)
            }
            else {
                if(st.length > 0) st.pop()
            }
        })

        return st.join("")
    }

    return refine(s) === refine(t)
};
```