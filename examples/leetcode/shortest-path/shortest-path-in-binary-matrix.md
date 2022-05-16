# 1. 설명
- 최단 경로를 구하세요.


[문제 링크](https://leetcode.com/problems/shortest-path-in-binary-matrix/)

# 2. 코드
### 1) Python
```python
   from collections import deque
from typing import List

"""
시간 복잡도: O(n^2)
공간 복잡도: O(n^2)
사용한 알고리즘: BFS(최단경로)
사용한 자료구조: 그래프
"""


class Solution:
    def shortestPathBinaryMatrix(self, grid: List[List[int]]) -> int:
        # 1. init
        n = len(grid)
        m = len(grid[0])
        check = [[-1 for _ in range(m)] for _ in range(n)]
        d = [(-1, -1), (-1, 0), (-1, 1), (0, 1), (1, 1), (1, 0), (1, -1), (0, -1)]

        # 2. bfs
        def bfs(x, y):
            if grid[x][y] != 0: return

            check[x][y] = 1
            q = deque([(x, y)])

            while q:
                x, y = q.popleft()

                for dx, dy in d:
                    nx, ny = x + dx, y + dy
                    if nx < 0 or nx >= n or ny < 0 or ny >= m: continue
                    if grid[nx][ny] != 0 or check[nx][ny] != -1: continue

                    check[nx][ny] = check[x][y] + 1
                    q.append((nx, ny))

        bfs(0, 0)

        return check[n-1][m-1]
```

### 2) Java
```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public int shortestPathBinaryMatrix(int[][] grid) {
        // 1. init
        int n = grid.length;
        int m = grid[0].length;

        return bfs(0, 0, grid, n, m);
    }

    public int bfs(int x, int y, int[][] grid, int n, int m) {
        // 1) init
        int[][] check = new int[n][m];
        for(int i=0; i<n; i++)
            for(int j=0; j<m; j++)
                check[i][j] = -1;

        int[][] d = {{-1, -1}, {-1, 0}, {-1, 1}, {0, 1}, {1, 1}, {1, 0}, {1, -1}, {0, -1}};


        // 2) bfs
        Queue<Point> q = new LinkedList<>();
        if(grid[x][y] == 0) {
            q.add(new Point(x, y));
            check[x][y] = 1;
        }

        while(!q.isEmpty()) {
            Point cur = q.poll();
            x = cur.x;
            y = cur.y;

            for(int[] dd: d) {
                int nx = x + dd[0];
                int ny = y + dd[1];

                if(nx < 0 || nx >= n || ny < 0 || ny >= m) continue;
                if(grid[nx][ny] != 0 || check[nx][ny] != -1) continue;

                check[nx][ny] = check[x][y] + 1;
                q.add(new Point(nx, ny));
            }
        }

        return check[n-1][m-1];
    }
}

class Point {
    int x, y;

    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```

### 3) JavaScript
```js
const shortestPathBinaryMatrix = (grid) => {
    // 1. init
    const n = grid.length
    const m = grid[0].length
    const check = Array.from(new Array(n), () => new Array(m).fill(-1))
    const d = [[-1, -1], [-1, 0], [-1, 1], [0, 1], [1, 1], [1, 0], [1, -1], [0, -1]]

    // 2. bfs
    const bfs = (startX, startY) => {
        const q = []
        if(grid[startX][startY] === 0) {
            check[startX][startY] = 1
            q.push([startX, startY])
        }

        while(q.length > 0) {
            const [x, y] = q.shift()

            for(const [dx, dy] of d) {
                const nx = x + dx
                const ny = y + dy
                if(nx < 0 || nx >= n || ny < 0 || ny >= m) continue
                if(grid[nx][ny] !== 0 || check[nx][ny] !== -1) continue

                check[nx][ny] = check[x][y] + 1
                q.push([nx, ny])
            }
        }

        return check[n-1][m-1]
    }

    return bfs(0, 0)
};
```

### 4) TypeScript
```ts
const shortestPathBinaryMatrix = (grid: number[][]): number => {
    // 1. init
    const n: number = grid.length
    const m: number = grid[0].length
    const check: number[][] = Array.from(new Array(n), () => new Array(m).fill(-1))
    const d: number[][] = [[-1, -1], [-1, 0], [-1, 1], [0, 1], [1, 1], [1, 0], [1, -1], [0, -1]]

    // 2. bfs
    const bfs = (startX:number, startY:number): number => {
        const q: [number, number][] = []
        if(grid[startX][startY] === 0) {
            check[startX][startY] = 1
            q.push([startX, startY])
        }

        while(q.length > 0) {
            const [x, y] = q.shift()

            for(const [dx, dy] of d) {
                const nx = x + dx
                const ny = y + dy
                if(nx < 0 || nx >= n || ny < 0 || ny >= m) continue
                if(grid[nx][ny] !== 0 || check[nx][ny] !== -1) continue

                check[nx][ny] = check[x][y] + 1
                q.push([nx, ny])
            }
        }

        return check[n-1][m-1]
    }

    return bfs(0, 0)
};
```