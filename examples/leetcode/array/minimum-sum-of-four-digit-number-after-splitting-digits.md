# 1. 설명
- 길이 4 정수의 2개의 페어의 합이 최소가 되는 합을 반환하세요



[문제 링크](https://leetcode.com/problems/minimum-sum-of-four-digit-number-after-splitting-digits/)

# 2. 코드
### 1) Python
```python
class Solution:
    def minimumSum(self, num: int) -> int:
        # 1. init
        s = sorted(str(num))

        
        return int(s[0]) * 10 + int(s[2]) + int(s[1]) * 10 + int(s[3])
```

### 2) Java
```java
class Solution {
    public int minimumSum(int num) {
        int[] s = Arrays.stream(Integer.toString(num).split(""))
                .map(Integer::parseInt)
                .sorted(Comparator.comparingInt(a -> a))
                .mapToInt(Integer::intValue).toArray();

        return (s[0] + s[1]) * 10 + s[2] + s[3];
    }
}
```

### 3) JavaScript
```js
const minimumSum = (num) => {
    const s = String(num).split("")
        .map(x => Number(x))
        .sort((a, b) => a - b)


    return (s[0] + s[1]) * 10 + s[2] + s[3]
};
```