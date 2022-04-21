# 1. 설명
- 문자열에 포함된 숫자가 증가하는지 여부를 반환하세요


[문제 링크](https://leetcode.com/problems/check-if-numbers-are-ascending-in-a-sentence/)


# 2. 코드
### 1) Python
```python
class Solution:
    def areNumbersAscending(self, s: str) -> bool:

        s = re.sub("[^0-9 ]", "", s).strip()
        s_list = [int(x) for x in re.split(" +", s)]

        prev = -1
        for c in s_list:
            if not prev < c: return False
            prev = c

        return True
```

### 2) Java
```java
class Solution {
    public boolean areNumbersAscending(String s) {
        s = s.replaceAll("[^0-9 ]", "").trim();
        int[] l = Arrays.stream(s.split(" +"))
                .map(Integer::parseInt)
                .mapToInt(x -> x).toArray();

        int prev = -1;
        for(int c: l) {
            if(prev >= c) return false;
            prev = c;
        }

        return true;
    }
}
```

### 3) JavaScript
```js
const areNumbersAscending = (s) => {
    s = s.replace(/[^0-9 ]/g, '').trim()

    const l = s.split(/ +/).map(x => Number(x))

    let prev = -1
    for(const c of l) {
        if(prev >= c) return false
        prev = c
    }

    return true
};
```