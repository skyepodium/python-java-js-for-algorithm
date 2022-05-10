# 1. 설명
- 1차원 배열을 2차원으로 변경하세요

[문제 링크](https://leetcode.com/problems/convert-1d-array-into-2d-array/)

# 2. 코드
### 1) Python
```python
from typing import List


class Solution:
    def construct2DArray(self, original: List[int], m: int, n: int) -> List[List[int]]:
        if len(original) != m * n: return []

        # 1. init
        res = []

        # 2. loop
        cnt = 0
        t = []
        for o in original:
            t.append(o)
            cnt += 1
            if cnt >= n:
                cnt = 0
                res.append(t[::])
                t = []

        return res
```

### 2) Java
```java
class Solution {
    public int[][] construct2DArray(int[] original, int m, int n) {
        // 0. exception
        if(original.length != m * n) return new int[0][0];

        // 1. init
        int res[][] = new int[m][n];

        // 2. loop
        int i=0;
        int j=0;
        for(int o: original) {
            res[i][j] = o;
            j++;
            if(j >= n) {
                j = 0;
                i++;
            }
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const construct2DArray = (original, m, n) => {
    // 0. exception
    if(original.length !== m * n) return []

    // 1. init
    const res = []

    // 2. loop
    let cnt = 0
    let t = []
    original.forEach(o => {
        t.push(o)
        cnt++
        if(cnt >= n) {
            cnt = 0
            res.push([...t])
            t = []
        }
    })

    return res
};
```

### 4) TypeScript
```ts
const construct2DArray = (original: number[], m: number, n: number): number[][] => {
    // 0. exception
    if(original.length !== m * n) return []

    // 1. init
    const res:number[][] = []

    // 2. loop
    let cnt:number = 0
    let t:number[] = []
    original.forEach(o => {
        t.push(o)
        cnt++
        if(cnt >= n) {
            cnt = 0
            res.push([...t])
            t = []
        }
    })

    return res
};
```