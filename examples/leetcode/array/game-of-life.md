# 1. 설명
- 규칙에 따라 board를 재구성하세요



[문제 링크](https://leetcode.com/problems/game-of-life/)

# 2. 코드
### 1) Python
```python
class Solution:
    def gameOfLife(self, board: List[List[int]]) -> None:
        # 1. init
        n = len(board)
        m = len(board[0])
        d = [(-1, 0), (-1, 1), (0, 1), (1, 1), (1, 0), (1, -1), (0, -1), (-1, -1)]
        a = [[0 for _ in range(m)] for _ in range(n)]

        # 2. loop
        for i in range(n):
            for j in range(m):
                cur = board[i][j]
                cnt = 0

                for dx, dy in d:
                    nx, ny = i + dx, j + dy
                    if nx < 0 or nx >= n or ny < 0 or ny >= m: continue

                    ne = board[nx][ny]
                    if ne == 1: cnt += 1

                if cur == 1:
                    if 2 <= cnt <= 3: a[i][j] = 1
                else:
                    if cnt == 3: a[i][j] = 1

        # 3. copy
        for i in range(n):
            for j in range(m):
                board[i][j] = a[i][j]
```

### 2) Java
```java
class Solution {
    public void gameOfLife(int[][] board) {
        // 1. init
        int n = board.length;
        int m = board[0].length;
        int[][] d = {{-1, 0}, {-1, 1}, {0, 1}, {1, 1}, {1, 0}, {1, -1}, {0, -1}, {-1, -1}};
        int[][] a = new int[n][m];

        // 2. loop
        for(int i=0; i<n; i++) {
            for(int j=0; j<m; j++) {
                int cur = board[i][j];
                int cnt = 0;

                for(int[] dd: d) {
                    int nx = i + dd[0];
                    int ny = j + dd[1];

                    if(nx < 0 || nx >= n || ny < 0 || ny >= m) continue;

                    int ne = board[nx][ny];

                    if(ne == 1) cnt += 1;
                }

                if(cur == 1) {
                    if(cnt >= 2 && cnt <= 3) a[i][j] = 1;
                }
                else {
                    if(cnt == 3) a[i][j] = 1;
                }
            }
        }

        // 3. copy
        for(int i=0; i<n; i++) {
            for(int j=0; j<m; j++) {
                board[i][j] = a[i][j];
            }
        }
    }
}
```

### 3) JavaScript
```js
const gameOfLife = (board) => {
    // 1. init
    const n = board.length
    const m = board[0].length
    const d = [[-1, 0], [-1, 1], [0, 1], [1, 1], [1, 0], [1, -1], [0, -1], [-1, -1]]
    const a = Array.from(Array(n), () => new Array(m).fill(0))

    // 2. loop
    for(let i=0; i<n; i++) {
        for(let j=0; j<m; j++) {
            const cur = board[i][j]
            let cnt = 0

            for(const [dx, dy] of d) {
                const nx = i + dx
                const ny = j + dy
                if(nx < 0 || nx >= n || ny < 0 || ny >= m) continue

                const ne = board[nx][ny]

                if(ne === 1) cnt += 1
            }

            if(cur === 1) {
                if(cnt >= 2 && cnt <= 3) a[i][j] = 1
            }
            else {
                if(cnt === 3) a[i][j] = 1
            }
        }
    }

    // 3. copy
    for(let i=0; i<n; i++) {
        for(let j=0; j<m; j++) {
            board[i][j] = a[i][j]
        }
    }
};
```