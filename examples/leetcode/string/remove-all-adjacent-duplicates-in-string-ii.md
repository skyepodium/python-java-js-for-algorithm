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

```

### 3) JavaScript
```js

```