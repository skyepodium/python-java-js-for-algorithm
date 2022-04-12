# 1. 설명
- 타켓보다 큰 최소 글자를 구하세요


[문제 링크](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)

# 2. 코드
### 1) python
```python
class Solution:
    def nextGreatestLetter(self, letters: List[str], target: str) -> str:
        # 1. init
        res = letters[0]
        t = ord(target)
        val = 1000

        # 2. loop
        for l in letters:
            c = ord(l)
            if t < c < val:
                res = l
                val = c

        return res
```

### 2) Java
```java
class Solution {
    public char nextGreatestLetter(char[] letters, char target) {
        // 1. init
        char res = letters[0];
        int val = 1000;
        int t = target;

        // 2. loop
        for(char l: letters) {
            int c = l;
            if(c > t && c < val) {
                res = l;
                val = c;
            }
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const nextGreatestLetter = (letters, target) => {
    // 1. init
    let res = letters[0]
    const t = target.charCodeAt(0)
    let val = 1000

    // 2. loop
    letters.forEach(x => {
        const c = x.charCodeAt(0)
        if(c > t && c < val) {
            res = x
            val = c
        }
    })

    return res
};
```