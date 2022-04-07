# 1. 설명
- prefix가 포함된 문자열의 개수를 구하세요



[문제 링크](https://leetcode.com/problems/counting-words-with-a-given-prefix/)

# 2. 코드
### 1) Python
```python
def prefixCount(self, words: List[str], pref: str) -> int:
    return sum([1 if w.find(pref) == 0 else 0 for w in words])
```

### 2) Java
```java
class Solution {
    public int prefixCount(String[] words, String pref) {
        return Arrays.stream(words).map(x -> x.indexOf(pref) == 0 ? 1 : 0)
                .reduce(Integer::sum)
                .get();
    }
}
```

### 3) JavaScript
```js
const prefixCount = (words, pref) => {

    return words.map(x => x.indexOf(pref) === 0 ? 1 : 0)
        .reduce((prev, cur) => prev + cur)
};
```