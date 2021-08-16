# 1. 설명
- '(', ')', '{', '}', '[', ']' 로 구성된 올바른 괄호문자열 여부를 반환하세요.

- 배열의 길이 1 <= n <= 1만



[문제 링크](https://leetcode.com/problems/valid-parentheses/submissions/)

# 2. 코드
### 1) python
```python
class Solution:
    def isValid(self, s: str) -> bool:

        # 1. 시작 괄호를 기준으로 딕셔너리 생성
        d = {
            '(': ')',
            '{': '}',
            '[': ']'
        }

        # 2. 스택
        stack = []

        for c in s:
            # 3. 스택에 들어있는 경우
            if stack:
                # 현재가 시작 괄호이면 push
                if c in d:
                    stack.append(c)
                # 현재가 닫는 괄호인데 top의 닫는 괄호가 아니면 종료
                else:
                    if d[stack.pop()] != c:
                        return False
            # 4. 스택이 비어있는 경우
            else:
                stack.append(c)
                # 현재가 닫는 괄호인면 종료
                if c not in d:
                    return False

        # 5. 여는 괄호가 하나라도 남아있으면 종료
        if stack:
            return False

        return True
```

### 2) java
```java
class Solution {
    public boolean isValid(String s) {

        // 1. 여는 괄호 기준으로 닫는 괄호 map 생성
        HashMap<Character, Character> map = new HashMap<>();
        map.put('{', '}');
        map.put('[', ']');
        map.put('(', ')');

        // 2. 스택 생성
        Stack<Character> stack = new Stack<>();

        int size = s.length();
        for(int i=0; i<size; i++) {
            char cur = s.charAt(i);

            // 3. 스택이 들어있는 경우
            if(!stack.empty()) {

                // 현재가 시작 괄호이면 push
                if(map.get(cur) != null) {
                    stack.add(cur);
                }
                // 현재가 닫는 과로인데 top의 닫는 괄호가 아니면 종료
                else {
                    if(map.get(stack.pop()) != cur) return false;
                }
            }
            // 4. 스택이 비어있는 경우
            else{
                stack.add(cur);
                // 현재가 닫는 괄호이면 종료
                if(map.get(cur) == null) return false;
            }
        }

        // 5. 여는 괄호가 하나라도 남아있으면 종료
        if(!stack.empty()) return false;

        return true;
    }
}
```