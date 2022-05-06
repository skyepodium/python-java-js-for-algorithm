# 연속적인 중복 제거 - stack

문자열에서 연속적으로 중복을 제거하는 경우가 있습니다.

### 1) 예시
```
abbac -> aac -> c
```

### 2) stack
이러한 경우 스택을 사용하면 쉽게 해결할 수 있습니다.

왜냐하면 stack은 top의 자료를 O(1)만에 확인 할 수 있기 때문에 연속적인 중복제거에 활용할 수 있습니다.

### 3) 2leetcode 예제
- [remove-all-adjacent-duplicates-in-string](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)  
- [remove-all-adjacent-duplicates-in-string-ii](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string-ii/)

# 1. Python
```python
s = "abbac"

st = []

for c in s:
    if st and st[-1] == c:
        while st and st[-1] == c: st.pop()
    else:
        st.append(c)

res = "".join(st)

print('res', res) # c
```

# 2. Java
```java
import java.util.Stack;

class Main {
    public static void main(String[] args) {
        String s = "abbac";

        Stack<Character> st = new Stack<>();

        for(int i=0; i<s.length(); i++) {
            char c = s.charAt(i);

            if(st.size() > 0 && st.peek() == c) {
                while(st.size() > 0 && st.peek() == c) st.pop();
            }
            else {
                st.add(c);
            }
        }

        StringBuilder res = new StringBuilder();
        while(!st.isEmpty()) res.append(st.pop());

        System.out.println(res.reverse()); // c
    }
}
```

# 3. JavaScript
```js
const s = "abbac"

const st = []

s.split("").forEach(c => {
    if(st.length > 0 && st[st.length - 1] === c) {
        while(st.length > 0 && st[st.length - 1] === c) st.pop()
    }
    else {
        st.push(c)
    }
})

const res = st.join("")

console.log('res', res) // c
```

### 4. TypeScript
```ts
const s:string = "abbac"

const st:string[] = []

s.split("").forEach(c => {
    if(st.length > 0 && st[st.length - 1] === c) {
        while(st.length > 0 && st[st.length - 1] === c) st.pop()
    }
    else {
        st.push(c)
    }
})

const res:string = st.join("")

console.log('res', res) // c
```