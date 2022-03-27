# 1. 설명
- 2진법으로 변환하고 1의 개수를 구하세요


[문제 링크](https://leetcode.com/problems/counting-bits/)

# 2. 코드
### 1) python
```python
class Solution:
    def countBits(self, n: int) -> List[int]:
        return [str(bin(x)).count('1') for x in [x for x in range(n+1)]]
```

### 2) java
```java
class Solution {
    public int[] countBits(int n) {
        return IntStream
                .range(0, n+1)
                .map(x -> {
                    int count = 0;
                    while(x > 0) {
                        if(x%2 == 1) count++;
                        x /= 2;
                    }
                    return count;
                })
                .toArray();
    }
}
```

### 3) JavaScript
```js
const countBits = (n) => {
    return Array.from(new Array(n+1).keys())
        .map(x => {
            let res = 0
            while(x > 0) {
                if(x%2 === 1) res++
                x = ~~(x/2)
            }
            return res
        })
};
```