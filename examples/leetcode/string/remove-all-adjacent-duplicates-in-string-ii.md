# 1. 설명
- 문자열에서 k개가 연속된 문자 중복을 제거하세요


[문제 링크](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string-ii/)


# 2. 코드
### 1) Python
```python
class Solution:
    def removeDuplicates(self, s: str, k: int) -> str:
        # 1. init
        st = []

        # 2. loop
        for c in s:
            if st:
                t, cnt = st[-1]
                if t == c:
                    if cnt == k - 1:
                        while st and st[-1][0] == c:
                            st.pop()
                    else:
                        st.append((c, cnt + 1))
                else:
                    st.append((c, 1))
            else:
                st.append((c, 1))

        return "".join([t for t, _ in st])
```

### 2) Java
```java
import java.util.Stack;

class Solution {
    public String removeDuplicates(String s, int k) {
        // 1. init
        Stack<Info> st = new Stack<>();

        // 2. loop
        for(int i=0; i<s.length(); i++) {
            char c = s.charAt(i);

            if(st.size() > 0) {
                Info cur = st.peek();
                char t = cur.c;
                int cnt = cur.cnt;
                if(t == c) {
                    if(cnt == k-1) {
                        while(st.size() > 0 && st.peek().c == c) {
                            st.pop();
                        }
                    }
                    else {
                        st.add(new Info(c, cnt + 1));
                    }
                }
                else {
                    st.add(new Info(c, 1));
                }
            }
            else {
                st.add(new Info(c, 1));
            }
        }

        // 3. res
        StringBuilder res = new StringBuilder();
        while(st.size() > 0) res.append(st.pop().c);

        return res.reverse().toString();
    }
}

class Info {
    char c;
    int cnt;
    public Info(char c, int cnt) {
        this.c = c;
        this.cnt = cnt;
    }
}
```

### 3) JavaScript
```js
const removeDuplicates = (s, k) => {
    // 1. init
    const st = []

    // 2. loop
    s.split("").forEach(c => {
        if(st.length > 0) {
            const [t, cnt] = st[st.length - 1]
            if(t === c) {
                if(cnt === k-1) {
                    while(st.length > 0 && st[st.length - 1][0] === c) st.pop()
                }
                else {
                    st.push([c, cnt + 1])
                }
            }
            else {
                st.push([c, 1])
            }
        }
        else {
            st.push([c, 1])
        }
    })

    return st.map(x => x[0]).join("")
};
```

### 4) TypeScript
```ts
const removeDuplicates = (s: string, k: number): string  => {
    // 1. init
    const st:[string, number][] = []

    // 2. loop
    s.split("").forEach(c => {
        if(st.length > 0) {
            const [t, cnt] = st[st.length - 1]
            if(t === c) {
                if(cnt === k-1) {
                    while(st.length > 0 && st[st.length - 1][0] === c) st.pop()
                }
                else {
                    st.push([c, cnt + 1])
                }
            }
            else {
                st.push([c, 1])
            }
        }
        else {
            st.push([c, 1])
        }
    })

    return st.map(x => x[0]).join("")
};
```