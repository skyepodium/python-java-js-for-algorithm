# 1. 설명
- 목적지에 도착하는 최소 비용을 구하세요


[문제 링크](https://leetcode.com/problems/path-with-minimum-effort/)

# 2. 코드
### 1) Python
```python
from typing import List
from heapq import heappush, heappop

class Solution:
    def minimumEffortPath(self, heights: List[List[int]]) -> int:
        # 1. init
        max_val = int(1e6)
        n = len(heights)
        m = len(heights[0])
        d = [[max_val for _ in range(m)] for _ in range(n)]
        dir = [(0, -1), (0, 1), (1, 0), (-1, 0)]

        # 2. dijkstra
        def dijkstra(start_x, start_y):
            pq = []
            d[start_x][start_y] = 0
            heappush(pq, (0, start_x, start_y))

            while pq:
                cost, x, y = heappop(pq)

                if d[x][y] < cost: continue

                for dx, dy in dir:
                    nx, ny = x + dx, y + dy
                    if nx < 0 or nx >= n or ny < 0 or ny >= m: continue

                    n_cost = max(abs(heights[nx][ny] - heights[x][y]), d[x][y])
                    if d[nx][ny] > n_cost:
                        d[nx][ny] = n_cost
                        heappush(pq, (d[nx][ny], nx, ny))

        dijkstra(0, 0)

        return d[n-1][m-1]
```

### 2) Java
```java
import java.util.Comparator;
import java.util.PriorityQueue;

class Solution {
    int n, m;
    int[][] d;
    int[][] dir = {{0, -1}, {0, 1}, {1, 0}, {-1, 0}};
    public int minimumEffortPath(int[][] heights) {
        // 1. init
        int maxVal = 1000000;
        n = heights.length;
        m = heights[0].length;
        d = new int[n][m];
        for(int i=0; i<n; i++)
            for(int j=0; j<m; j++)
                d[i][j] = maxVal;

        // 2. dijkstra
        dijkstra(0, 0, heights);

        return d[n-1][m-1];
    }

    public void dijkstra(int startX, int startY, int[][] heights) {
        PriorityQueue<Point> pq = new PriorityQueue<>(Comparator.comparingInt(a -> a.cost));
        d[startX][startY] = 0;
        pq.add(new Point(startX, startY, 0));

        while(!pq.isEmpty()) {
            Point cur = pq.poll();
            int x = cur.x;
            int y = cur.y;
            int cost = cur.cost;

            if(d[x][y] < cost) continue;

            for(int[] da: dir) {
                int nx = x + da[0];
                int ny = y + da[1];

                if(nx < 0 || nx >= n || ny < 0 || ny >= m) continue;

                int nCost = Math.max(Math.abs(heights[nx][ny] - heights[x][y]), d[x][y]);

                if(d[nx][ny] > nCost) {
                    d[nx][ny] = nCost;
                    pq.add(new Point(nx, ny, d[nx][ny]));
                }
            }
        }
    }
}

class Point {
    int x, y, cost;
    public Point(int x, int y, int cost) {
        this.x = x;
        this.y = y;
        this.cost = cost;
    }
}
```

### 3) JavaScript
```js
const minimumEffortPath = (heights) => {
    // 1. init
    const maxVal = Number(1e6)
    const n = heights.length
    const m = heights[0].length
    const d = Array.from(new Array(n), () => new Array(m).fill(maxVal))
    const dir = [[0, -1], [0, 1], [1, 0], [-1, 0]]

    // 2. dijkstra
    const dijkstra = (startX, startY) => {
        const q = []
        d[startX][startY] = 0
        q.push([startX, startY, 0])

        while(q.length > 0) {
            const [x, y, cost] = q.shift()

            if(d[x][y] < cost) continue

            for(const [dx, dy] of dir) {
                const nx = x + dx
                const ny = y + dy
                if(nx < 0 || nx >= n || ny < 0 || ny >= m) continue

                const nCost = Math.max(Math.abs(heights[nx][ny] - heights[x][y]), d[x][y])
                if(d[nx][ny] > nCost) {
                    d[nx][ny] = nCost
                    q.push([nx, ny, nCost])
                }
            }
        }
    }

    dijkstra(0, 0)

    return d[n-1][m-1]
};
```