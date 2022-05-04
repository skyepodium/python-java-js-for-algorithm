# 1. 설명
- 직선 여부를 반환하세요

[문제 링크](https://leetcode.com/problems/check-if-it-is-a-straight-line/)

# 2. 코드
### 1) Python
```python
from typing import List


class Solution:
    def checkStraightLine(self, coordinates: List[List[int]]) -> bool:
        # 1. init
        n = len(coordinates)

        # 2. ccw
        def ccw(r, p, q):
            first = (p[0] - r[0]) * (q[1] - r[1])
            second = (p[1] - r[1]) * (q[0] - r[0])
            result = first - second

            if result > 0:
                return 1
            elif result == 0:
                return 0
            else:
                return -1

        # 3. loop
        for i in range(n-2):
            if ccw(coordinates[i], coordinates[i+1], coordinates[i+2]) != 0:
                return False

        return True
```

### 2) Java
```java
class Solution {
    public boolean checkStraightLine(int[][] coordinates) {
        // 1. init
        int n = coordinates.length;

        // 2. loop
        for(int i=0; i<n-2; i++) {
            if(ccw(new Point(coordinates[i][0], coordinates[i][1]), new Point(coordinates[i+1][0], coordinates[i+1][1]), new Point(coordinates[i+2][0], coordinates[i+2][1])) != 0) return false;
        }

        return true;
    }

    public int ccw(Point p, Point q, Point r) {
        long first = (p.x - r.x) * (q.y - r.y);
        long second = (p.y - r.y) * (q.x - r.x);
        long result = first - second;

        if(result > 0) return 1;
        else if(result == 0) return 0;
        else return -1;
    }
}

class Point {
    long x, y;
    public Point(long x, long y) {
        this.x = x;
        this.y = y;
    }
}
```

### 3) JavaScript
```js
const checkStraightLine = (coordinates) => {
    // 1. init
    const n = coordinates.length

    // 2. ccw
    const ccw = (p, q, r) => {
        const first = (p[0] - r[0]) * (q[1] - r[1])
        const second = (p[1] - r[1]) * (q[0] - r[0])
        const result = first - second

        if(result > 0) return 1
        else if(result === 0) return 0
        else return -1
    }

    // 3. loop
    for(let i=0; i<n-2; i++) {
        if(ccw(coordinates[i], coordinates[i+1], coordinates[i+2]) !== 0) return false
    }

    return true
};
```

### 4) TypeScript
```ts
const checkStraightLine = (coordinates: number[][]): boolean => {

    // 1. init
    const n:number = coordinates.length

    // 2. ccw
    const ccw = (p:number[], q:number[], r:number[]):number => {
        const first:number = (p[0] - r[0]) * (q[1] - r[1])
        const second:number = (p[1] - r[1]) * (q[0] - r[0])
        const result:number = first - second

        if(result > 0) return 1
        else if(result === 0) return 0
        else return -1
    }

    // 3. loop
    for(let i=0; i<n-2; i++) {
        if(ccw(coordinates[i], coordinates[i+1], coordinates[i+2]) !== 0) return false
    }

    return true
};
```