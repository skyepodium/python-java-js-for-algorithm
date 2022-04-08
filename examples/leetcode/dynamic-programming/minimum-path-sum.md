# 1. 설명
- 왼쪽 상단에서 오른쪽 하단으로 가는 최단 경로를 구하세요

[문제 링크](https://leetcode.com/problems/minimum-path-sum/)

# 2. 코드
### 1) python
```python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        # 1. init
        n = len(grid)
        m = len(grid[0])
        MAX_VAL = 4000000
        d = [[MAX_VAL for _ in range(m)] for _ in range(n)]
        d[0][0] = grid[0][0]

        # 2. loop
        for i in range(n):
            for j in range(m):
                if i == 0 and j == 0: continue

                top_val = d[i-1][j] if i - 1 >= 0 else MAX_VAL
                left_val = d[i][j-1] if j - 1 >= 0 else MAX_VAL
                d[i][j] = min(top_val, left_val) + grid[i][j]

        return d[n-1][m-1]
```

### 2) Java
```java

```