# 1. 설명
- 모든 점을 연결하는 최소 비용을 구하세요


[문제 링크](https://leetcode.com/problems/min-cost-to-connect-all-points/)

# 2. 코드
### 1) Python
```python
from typing import List

class Solution:
    def minCostConnectPoints(self, points: List[List[int]]) -> int:
        # 1. init
        n = len(points)
        e = []
        d = [i for i in range(n)]
        res = 0

        # 2. cal_dist
        def cal_dist(first, second):
            x, y = first
            a, b = second
            return abs(x-a) + abs(y-b)

        # 3. make graph
        for i in range(n):
            for j in range(i+1, n):
                e.append((i, j, cal_dist(points[i], points[j])))

        # 4. sort
        e.sort(key=lambda x: x[2])

        # 5. find
        def find(node):
            if node == d[node]:
                return node
            else:
                d[node] = find(d[node])
                return d[node]

        # 6. cal cost
        for a, b, cost in e:
            a, b = find(a), find(b)
            if a != b:
                d[a] = b
                res += cost

        return res
```

### 2) Java
```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;

class Solution {
    int[] d;
    public int minCostConnectPoints(int[][] points) {
        // 1. init
        int n = points.length;
        d = new int[n];
        for(int i=0; i<n; i++) d[i] = i;
        List<Point> l = new ArrayList<>();
        int res = 0;

        // 2. make graph
        for(int i=0; i<n; i++) {
            for(int j=i+1; j<n; j++) {
                int dist = Math.abs(points[i][0] - points[j][0]) + Math.abs(points[i][1] - points[j][1]);
                l.add(new Point(i, j, dist));
            }
        }

        // 3. sort
        l.sort(Comparator.comparingInt(a -> a.cost));

        // 4. cost
        for(Point p: l) {
            int s = find(p.start);
            int e = find(p.end);
            int c = p.cost;

            if(s != e) {
                d[s] = e;
                res += c;
            }
        }

        return res;
    }

    public int find(int node) {
        if(node == d[node]) return node;
        else return d[node] = find(d[node]);
    }
}

class Point {
    int start;
    int end;
    int cost;
    public Point(int start, int end, int cost) {
        this.start = start;
        this.end = end;
        this.cost = cost;
    }
}
```

### 3) JavaScript
```js
const minCostConnectPoints = (points) => {
    // 1. init
    const n = points.length
    const e = []
    let res = 0
    const d = Array.from(Array(n).keys())

    // 2. calDist
    const calDist = (x, y, a, b) => {
        return Math.abs(x - a) + Math.abs(y-b)
    }

    // 3. make graph
    for(let i=0; i<n; i++) {
        for(let j=i+1; j<n; j++) {
            const [x, y] = points[i]
            const [a, b] = points[j]
            e.push([i, j, calDist(x, y, a, b)])
        }
    }

    // 4. sort
    e.sort((a, b) => a[2] - b[2])

    // 5. find
    const find = node => {
        if(node === d[node]) return node
        else return d[node] = find(d[node])
    }

    // 6. cost
    for(let [a, b, cost] of e) {
        a = find(a)
        b = find(b)
        if(a !== b) {
            d[a] = b
            res += cost
        }
    }

    return res
};
```