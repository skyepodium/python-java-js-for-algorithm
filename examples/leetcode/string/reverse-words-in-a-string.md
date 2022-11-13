# 1. 설명
- 문자열의 앞뒤 공백 제거한 결과 문자열을 공백 기준으로 배열로 만들고 뒤집으세요

[문제 링크](https://leetcode.com/problems/reverse-words-in-a-string/)


# 2. 코드
### 1) python
```python
class Solution:
    def reverseWords(self, s: str) -> str:
        return ' '.join(s.strip().split()[::-1])
```

### 2) java
```java
class Solution {
    public String reverseWords(String s) {
        String[] stringArray = s.trim().split(" +");

        List<String> list = new ArrayList<>(Arrays.asList(stringArray));
        Collections.reverse(list);

        // list to string
        return String.join(" ", list);
    }
}
```

### 3) JavaScript
```js
const reverseWords = (s) => {
    return s.trim().split(/ +/g).reverse().join(" ")
};
```