# 1. 설명
- 3개이상 연속된 문자를 2개로 줄이세요


[문제 링크](https://leetcode.com/problems/delete-characters-to-make-fancy-string/)


# 2. 코드
### 1) Python
```python
class Solution:
    def makeFancyString(self, s: str) -> str:
        # 1. init
        st = []

        # 2. loop
        for c in s:
            a, b = st[-1] if st else ('', 0)

            if a == c and b == 2: continue

            cnt = b + 1 if a == c else 1
            
            st.append((c, cnt))

        return "".join([a for a, b in st])
```

### 2) Java
```java
import java.util.Stack;
import java.util.stream.Collectors;

class Solution {
    public String makeFancyString(String s) {
        // 1. init
        Stack<Info> st = new Stack<>();

        // 2. loop
        for(String c: s.split("")) {
            Info cur = !st.isEmpty() ? st.peek() : new Info("", 0);

            String a = cur.c;
            int b = cur.cnt;

            if(a.equals(c) && b == 2) continue;

            int cnt = a.equals(c) ? b + 1 : 1;

            st.push(new Info(c, cnt));
        }

        return String.join("", st.stream().map(x -> x.c).collect(Collectors.toList()).toArray(new String[0]));
    }
}

class Info {
    String c;
    int cnt;
    public Info(String c, int cnt) {
        this.c = c;
        this.cnt = cnt;
    }
}
```

### 3) JavaScript
```js
const makeFancyString = (s) => {
    // 1. init
    const st = []

    // 2. loop
    for(const c of s.split("")) {
        const [a, b] = st.length > 0 ? st[st.length - 1] : ['', 0]

        if(a === c && b === 2) continue

        const cnt = a === c ? b + 1 : 1

        st.push([c, cnt])
    }

    return st.map(x => x[0]).join("")
};
```

### 4) TypeScript
```ts
const makeFancyString = (s:string):string => {
    // 1. init
    const st:[string, number][] = []

    // 2. loop
    for(const c of s.split("")) {
        const [a, b]:[string, number] = st.length > 0 ? st[st.length - 1] : ['', 0]

        if(a === c && b === 2) continue

        const cnt:number = a === c ? b + 1 : 1

        st.push([c, cnt])
    }

    return st.map(x => x[0]).join("")
};
```