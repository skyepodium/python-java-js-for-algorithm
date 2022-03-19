# 1. 설명
- 문자열이 모든 알파벳 단어를 적어도 1개씩 포함하는지 여부를 반환하세요.


[문제 링크](https://leetcode.com/problems/check-if-the-sentence-is-pangram/)


# 2. 코드
### 1) python
```python
class Solution:
    def checkIfPangram(self, sentence: str) -> bool:
        return len(set(sentence)) == 26
```

### 2) java
```java
class Solution {
    public boolean checkIfPangram(String sentence) {
        Set<Character> s = new HashSet<>();

        for(int i=0; i<sentence.length(); i++) {
            char c = sentence.charAt(i);
            s.add(c);
        }

        return s.size() == 26;
    }
}
```

### 3) JavaScript
```js
var checkIfPangram = function(sentence) {
    return new Set(sentence).size === 26
};
```