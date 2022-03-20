# 짧은 배열 반환

메서드의 리턴값을 길이 3이하의 배열을 만들어서 리턴하는 경우가 있습니다.

예시) [leetcode - convert-integer-to-the-sum-of-two-no-zero-integers](https://leetcode.com/problems/convert-integer-to-the-sum-of-two-no-zero-integers/)    

예시) [프로그래머스 - 영어 끝말잇기](https://programmers.co.kr/learn/courses/30/lessons/12981)

```java
class Solution {
    public int[] getNoZeroIntegers(int n) {

    }
}
```

### 1) python
파이썬은 리스트로 쉽게 가능합니다.
```python
def solution():
    return [0, 1]
```

### 2) java
자바는 초기화 값을 new와 함께 사용합니다.
```java
class Solution {
    public int[] solution() {
        return new int[]{0, 1};
    }
}
```

### 3) JavaScript
```js
const solution = () => {
    return [0, 1]
}
```