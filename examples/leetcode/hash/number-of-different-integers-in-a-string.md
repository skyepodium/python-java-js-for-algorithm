# 1. 설명
- 다른 숫자들의 개수를 반환하세요


[문제 링크](https://leetcode.com/problems/number-of-different-integers-in-a-string/)

# 2. 코드
### 1) python
```python
class Solution:
    def numDifferentIntegers(self, word: str) -> int:
        return len(set([int(x) for x in re.split("[a-z]", word) if x != '']))
```

### 2) java
```java
class Solution {
    public int numDifferentIntegers(String word) {
        Set<String> s = new HashSet<>();

        Arrays.stream(word.split("[a-z]"))
                .filter(x -> !"".equals(x))
                .forEach(x -> {
                    String val = removeLeadZero(x);
                    if(!s.contains(val)) s.add(val);
                });

        return s.size();
    }

    public String removeLeadZero(String s) {
        String res = s.replaceAll("^0+", "");
        return res.length() > 0 ? res : "0";
    }
}
```

### 3) JavaScript
```js
const numDifferentIntegers = (word) => {
    return new Set(word.split(/[a-z]+/g)
                .filter(x => x !== '')
                .map(x => BigInt(x))).size
};
```