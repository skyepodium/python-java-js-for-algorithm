# 1. 설명
- 중복된 문자를 제외한 결과중 사전순으로 가장 앞선 결과를 구하세요.



[문제 링크](https://leetcode.com/problems/remove-duplicate-letters/)

# 2. 코드
### 1) python
```python
from collections import Counter

class Solution:
    def removeDuplicateLetters(self, s: str) -> str:

        stack, counter, seen = [], Counter(s), set()

        for c in s:
            counter[c] -= 1

            if c in seen:
                continue

            while stack and c < stack[-1] and counter[stack[-1]] > 0:
                seen.remove(stack.pop())

            stack.append(c)
            seen.add(c)

        return "".join(stack)
```

### 2) java
```java
import java.util.HashSet;
import java.util.Stack;

class Solution {
    public String removeDuplicateLetters(String s) {
        // 1. init
        Stack<Character> st = new Stack<>();
        HashSet<Character> seen = new HashSet<>();
        int[] counter = new int[26];
        int size = s.length();

        // 2. count
        for(int i=0; i<size; i++) {
            char c = s.charAt(i);
            int order = c - 'a';
            counter[order]++;
        }

        // 3. loop
        for(int i=0; i<size; i++) {
            char c = s.charAt(i);
            int order = c - 'a';
            counter[order]--;

            if(seen.contains(c)) continue;

            while(!st.empty() && st.peek() > c && counter[st.peek() - 'a'] > 0) {
                seen.remove(st.pop());
            }

            seen.add(c);
            st.add(c);
        }

        // 4. return
        String res = "";
        while(!st.empty()) {
            res = st.pop() + res;
        }

        return res;
    }
}
```