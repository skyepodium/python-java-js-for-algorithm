# 1. 설명
- 규칙대로 생성되는 배열에서 최대값을 구하세요

[문제 링크](https://leetcode.com/problems/get-maximum-in-generated-array/)

# 2. 코드
### 1) Python
```python
class Solution:
    def getMaximumGenerated(self, n: int) -> int:
        # 1. init
        d = [0 for _ in range(n + 1)]
        max_val = 0
        if n >= 1:
            d[1] = 1
            max_val = 1

        # 2. loop
        for i in range(2, n + 1):
            mid = i // 2
            if mid * 2 == i:
                d[i] = d[mid]
            else:
                d[i] = d[mid] + d[mid + 1]

            max_val = max(max_val, d[i])

        return max_val
```

### 2) Java
```java
class Solution {
    public int getMaximumGenerated(int n) {
        // 1. init
        int[] d = new int[n+1];
        int maxVal = 0;
        if(n >= 1) {
            d[1] = 1;
            maxVal = 1;
        }

        // 2. tabulation
        for(int i=2; i<=n; i++) {
        int mid = i / 2;
            if(mid * 2 == i) d[i] = d[mid];
            else d[i] = d[mid] + d[mid + 1];

            maxVal = Math.max(maxVal, d[i]);
        }

        return maxVal;
    }
}
```

### 3) JavaScript
```js
const getMaximumGenerated = (n) => {
    // 1. init
    const d = Array.from(new Array(n+1)).fill(0)
    let maxVal = 0
    if(n >= 1) {
        d[1] = 1
        maxVal = 1
    }

    // 2. tabulation
    for(let i=2; i<=n; i++) {
        const mid = ~~(i / 2)
        if(mid * 2 === i) d[i] = d[mid]
        else d[i] = d[mid] + d[mid + 1]
        
        maxVal = Math.max(maxVal, d[i])
    }

    return maxVal
};
```