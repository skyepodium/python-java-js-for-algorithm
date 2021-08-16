# 1. 설명
- 땅 - 1, 물 - 0
- 섬의 개수를 구하세요.



[문제 링크](https://leetcode.com/problems/number-of-islands/)

# 2. 코드
### 1) python
```python
class Solution:
    def numIslands(self, grid: list[list[str]]) -> int:

        n = len(grid)
        m = len(grid[0])
        check = [[False for _ in range(m)] for _ in range(n)]
        d = (0, -1), (0, 1), (1, 0), (-1, 0)

        cnt = 0

        def dfs(x, y):
            check[x][y] = True

            for dx, dy in d:
                nx, ny = x + dx, y + dy

                if nx < 0 or nx >= n or ny < 0 or ny >= m:
                    continue

                if grid[nx][ny] == "1" and not check[nx][ny]:
                    dfs(nx, ny)

        for i in range(n):
            for j in range(m):
                if grid[i][j] == "1" and not check[i][j]:
                    dfs(i, j)
                    cnt += 1

        return cnt
```

### 2) java
```java
class Solution {

    public int[][] check;
    public char[][] a;
    public int n, m, cnt;
    public int[] dx = {0, 0, 1, -1};
    public int[] dy = {-1, 1, 0, 0};

    public int numIslands(char[][] grid) {

        n = grid.length;
        m = grid[0].length;

        check = new int[n][m];

        a = grid;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (a[i][j] == '1' && check[i][j] == 0) {
                    dfs(i, j);
                    cnt++;
                }
            }
        }
        return cnt;
    }

    public void dfs(int x, int y) {
        check[x][y] = 1;

        for(int i=0; i<4; i++) {
            int nx = x + dx[i];
            int ny = y + dy[i];

            if(nx < 0 || nx >= n || ny < 0 || ny >= m) continue;

            if(a[nx][ny] == '1' && check[nx][ny] == 0) {
                dfs(nx, ny);
            }
        }
    }
}
```