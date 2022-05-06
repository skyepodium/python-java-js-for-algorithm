# 1. 설명
- 문자열에서 중복을 모두 제거하세요


[문제 링크](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)

# 참고
기억하자 문자열에서 중복제거할때 스택을 쓰면 정말 편리하다. 
스택의 특성인 top을 O(1)만에 확인 할 수 있음을 꼭 기억하자

# 2. 코드
### 1) Python
```python
class Solution:
    def removeDuplicates(self, s: str) -> str:
        # 1. init
        st = []

        # 2. loop
        for c in s:
            if st and st[-1] == c:
                while st and st[-1] == c:
                    st.pop()
            else:
                st.append(c)

        return "".join(st)
```

### 2) Java
```java
import java.util.Stack;

class Solution {
    public String removeDuplicates(String s) {
        // 1. init
        Stack<Character> st = new Stack<>();

        for(int i=0; i<s.length(); i++) {
            char c = s.charAt(i);

            st.add(c);

            while(st.size() > 0 && st.peek() == c) st.pop();
        }

        // 3. res
        StringBuilder res = new StringBuilder();
        while(st.size() > 0) res.append(st.pop());
        return res.reverse().toString();
    }
}
```

### 3) JavaScript
```js
const removeDuplicates = (s) => {
    // 1. init
    const st = []

    // 2. loop
    s.split("").forEach(c => {
        if(st.length > 0 && st[st.length - 1] === c) while(st.length > 0 && st[st.length - 1] === c) st.pop()
        else st.push(c)
    })

    return st.join("")
};
```

### 4) TypeScript
```ts
const removeDuplicates = (s: string): string => {
    // 1. init
    const st:string[] = []

    // 2. loop
    s.split("").forEach(c => {
        if(st.length > 0 && st[st.length - 1] === c) while(st.length > 0 && st[st.length - 1] === c) st.pop()
        else st.push(c)
    })

    return st.join("")
};
```