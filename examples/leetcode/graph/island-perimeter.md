# 1. 설명
- 섬 외각의 선분의 개수를 구하세요.



[문제 링크](https://leetcode.com/problems/island-perimeter/)

# 2. 코드
### 1) python
```python
from typing import List
from collections import deque

class Solution:
    def islandPerimeter(self, grid: List[List[int]]) -> int:
        # 1. init
        n, m = len(grid), len(grid[0])
        check = [[False for _ in range(m)] for _ in range(n)]
        d = (0, -1), (0, 1), (1, 0), (-1, 0)
        result = 0

        # 2. bfs
        def bfs(x, y):
            check[x][y] = True
            q = deque()
            cnt = 0
            link_cnt = 0
            q.append((x, y))

            while q:
                x, y = q.popleft()
                cnt += 1
                for dx, dy in d:
                    nx = x + dx
                    ny = y + dy
                    if nx < 0 or nx >= n or ny < 0 or ny >= m:
                        continue

                    if grid[nx][ny] == 1:
                        link_cnt += 1
                        if not check[nx][ny]:
                            check[nx][ny] = True
                            q.append((nx, ny))
            return cnt * 4 - link_cnt

        # 3. loop
        for i in range(n):
            for j in range(m):
                if grid[i][j] == 1 and not check[i][j]:
                    result += bfs(i, j)


        return result
```

### 2) java
```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public static int[] dx = {0, 0, 1, -1};
    public static int[] dy = {-1, 1, 0, 0};
    public static int n, m;
    public static int res = 0;
    public static boolean[][] check;
    public int islandPerimeter(int[][] grid) {
        // 1. init
        res = 0;
        n = grid.length;
        m = grid[0].length;
        check = new boolean[n][m];

        // 2. loop
        for(int i=0; i<n; i++) {
            for(int j=0; j<m; j++) {
                if(grid[i][j] == 1 && !check[i][j]) {
                    res += bfs(i, j, grid);
                }
            }
        }

        return res;
    }

    public int bfs(int x, int y, int[][] grid) {
        int cnt = 0;
        int linkCnt = 0;

        Queue<Info> q = new LinkedList<>();
        q.add(new Info(x, y));
        check[x][y] = true;

        while(!q.isEmpty()) {
            Info cur = q.poll();
            cnt++;
            x = cur.x;
            y = cur.y;

            for(int i=0; i<4; i++) {
                int nx = x + dx[i];
                int ny = y + dy[i];

                if(nx < 0 || nx >= n || ny < 0 || ny >= m) continue;

                if(grid[nx][ny] == 1) {
                    linkCnt++;
                    if(!check[nx][ny]) {
                        check[nx][ny] = true;
                        q.add(new Info(nx, ny));
                    }
                }
            }
        }

        return cnt * 4 - linkCnt;
    }
}

class Info {
    int x;
    int y;

    public Info(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```