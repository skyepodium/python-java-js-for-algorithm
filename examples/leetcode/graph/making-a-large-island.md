# 1. 설명
- 최대 1개의 0을 넣어서 만들 수 있는 섬의 최대 크기를 구하세요.


[문제 링크](https://leetcode.com/problems/making-a-large-island/)

# 비고
O(n^4) 가 아닌 O(n^2) 안에 풀어야한다.

# 2. 코드
### 1) python
```python
from collections import deque

class Solution:
    def largestIsland(self, grid: List[List[int]]) -> int:
        # 1. init
        n = len(grid)
        check = [[-1 for _ in range(n)] for _ in range(n)]
        d = [(0, -1), (0, 1), (1, 0), (-1, 0)]

        # 2. bfs
        def bfs(start_x, start_y, idx):
            check[start_x][start_y] = idx
            q = deque()
            q.append((start_x, start_y))
            cnt = 0

            while q:
                x, y = q.popleft()
                cnt += 1
                for dx, dy in d:
                    nx, ny = x + dx, y + dy
                    if nx < 0 or nx >= n or ny < 0 or ny >= n:
                        continue
                    if check[nx][ny] == -1 and grid[nx][ny] == 1:
                        check[nx][ny] = idx
                        q.append((nx, ny))
            return cnt

        # 3. loop
        idx = 0
        cnt_dict = {}
        for i in range(n):
            for j in range(n):
                if grid[i][j] == 1 and check[i][j] == -1:
                    cnt = bfs(i, j, idx)
                    cnt_dict[idx] = cnt
                    idx += 1

        # 4. loop
        res = 0
        for i in range(n):
            for j in range(n):
                if grid[i][j] == 0:
                    cur_cnt = 0
                    seen = set()
                    for dx, dy in d:
                        nx, ny = i + dx, j + dy

                        if nx < 0 or nx >= n or ny < 0 or ny >= n:
                            continue

                        if check[nx][ny] > -1 and check[nx][ny] not in seen:
                            n_idx = check[nx][ny]
                            n_cnt = cnt_dict[n_idx]
                            cur_cnt += n_cnt
                            seen.add(n_idx)
                    res = max(res, cur_cnt + 1)

        return res if res > 0 else n * n
```

### 2) java
```java
import java.util.HashMap;
import java.util.HashSet;
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    int n, idx, res = 0;
    int[][] check;
    int[] dx = {0, 0, 1, -1};
    int[] dy = {-1, 1, 0, 0};
    HashMap<Integer, Integer> m = new HashMap<>();
    public int largestIsland(int[][] grid) {
        // 1. init
        n = grid.length;
        check = new int[n+1][n+1];

        // 2. loop
        idx = 1;
        for(int i=0; i<n; i++) {
            for(int j=0; j<n; j++) {
                if(grid[i][j] == 1 && check[i][j] == 0) {
                    int curCnt = bfs(i, j, idx, grid);
                    m.put(idx, curCnt);
                    idx++;
                }
            }
        }

        // 3. loop
        for(int i=0; i<n; i++) {
            for(int j=0; j<n; j++) {
                if(grid[i][j] == 0) {

                    int sumCnt = 0;
                    HashSet<Integer> s = new HashSet<>();
                    for(int k = 0; k<4; k++) {
                        int nx = i + dx[k];
                        int ny = j + dy[k];

                        if(nx < 0 || nx >= n || ny < 0 || ny >= n) {
                            continue;
                        }

                        if(check[nx][ny] > 0 && !s.contains(check[nx][ny])){
                            int nIdx = check[nx][ny];
                            int curCnt = m.get(nIdx);
                            sumCnt += curCnt;
                            s.add(nIdx);
                        }
                    }
                    res = Math.max(res, sumCnt + 1);
                }
            }
        }

        return res > 0 ? res : n*n;
    }

    public int bfs(int startX, int startY, int idx, int[][] grid) {
        int cnt = 0;
        check[startX][startY] = idx;
        Queue<Info> q = new LinkedList<>();
        q.add(new Info(startX, startY));

        while(!q.isEmpty()) {
            Info cur = q.poll();
            int x = cur.x;
            int y = cur.y;
            cnt++;

            for(int i=0; i<4; i++){
                int nx = x + dx[i];
                int ny = y + dy[i];

                if(nx < 0 || nx >= n || ny < 0 || ny >= n) {
                    continue;
                }

                if(grid[nx][ny] == 1 && check[nx][ny] == 0) {
                    check[nx][ny] = idx;
                    q.add(new Info(nx, ny));
                }
            }
        }
        return cnt;
    }
}

class Info {
    int x, y;
    public Info(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```