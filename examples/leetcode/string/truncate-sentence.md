# 1. 설명
- 처음 ~ k번째의 단어만 포함한 문자열을 반환하세요.


[문제 링크](https://leetcode.com/problems/truncate-sentence/)


# 2. 코드
### 1) python
```python
class Solution:
    def truncateSentence(self, s: str, k: int) -> str:
        return " ".join(s.split(" ")[:k])
```

### 2) java
```java
class Solution {
    public String truncateSentence(String s, int k) {
        return String.join(" ", Arrays.copyOfRange(s.split(" "), 0, k));
    }
}
```