# 1. 설명
- 가장 높은 고도를 구하세요

[문제 링크](https://leetcode.com/problems/find-the-highest-altitude/)

# 2. 코드
### 1) Python
```python
class Solution:
    def largestAltitude(self, gain: List[int]) -> int:

        return max(0, max(accumulate(gain)))
```

### 2) Java
```java
class Solution {
    public int largestAltitude(int[] gain) {
        // 1. init
        int prev = 0;
        int res = 0;

        // 2. loop
        for(int g: gain) {
            prev = prev + g;
            res = Math.max(res, prev);
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const largestAltitude = (gain) => {
    // 1. init
    let prev = 0
    let res = 0

    // 2. loop
    gain.forEach(g => {
        prev = prev + g
        res = Math.max(res, prev)
    })

    return res
};
```

### 4) TypeScript
```ts
const largestAltitude = (gain: number[]): number =>{
    // 1. init
    let prev:number = 0
    let res:number = 0

    // 2. loop
    gain.forEach(g => {
        prev = prev + g
        res = Math.max(res, prev)
    })

    return res
};
```