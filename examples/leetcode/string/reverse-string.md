# 1. 설명
- 이 문제의 반환값은 없다.
- 배열을 뒤집어라
- 공간 복잡도 O(1)

- 문자열의 길이 1 <= n <= 10만


[문제 링크](https://leetcode.com/problems/reverse-string/)


# 2. 코드
### 1) python
- reverse는 내부를 변경한다.
- 슬라이싱 결과물에 [:]을 사용해야 값복사로 O(1)을 만족한다.
```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        s.reverse()
```
```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        s[:] = s[::-1]
```

### 2) java
투포인터, 스왑
```java
class Solution {
    public void reverseString(char[] s) {
        int size = s.length;
        
        int l = 0;
        int r = size - 1;
        
        while (l < r) {
            char temp = s[l];
            s[l] = s[r];
            s[r] = temp;
            
            l++;
            r--;
        }
    }
}
```

### 3) JavaScript
```js
var reverseString = function(s) {
    s = s.reverse()
};
```