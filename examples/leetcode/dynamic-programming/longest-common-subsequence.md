# 1. 설명
- 가장 긴 공통 부분 수열

[문제 링크](https://leetcode.com/problems/longest-common-subsequence/)

# 2. 코드
### 1) python
```python
class Solution:
    def longestCommonSubsequence(self, text1: str, text2: str) -> int:
        # 1. init
        n, m = len(text1), len(text2)
        d = [[0 for _ in range(m+1)] for _ in range(n+1)]

        # 2. loop
        for i in range(1, n+1):
            for j in range(1, m+1):
                if text1[i-1] == text2[j-1]:
                    d[i][j] = d[i-1][j-1] + 1
                else:
                    d[i][j] = max(d[i-1][j], d[i][j-1])

        return d[n][m]
```

### 2) java
```java
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        // 1. init
        int n = text1.length();
        int m = text2.length();
        int[][] d = new int[n+1][m+1];

        // 2. loop
        for(int i=1; i<=n; i++) {
            for(int j=1; j<=m; j++) {
                if(text1.charAt(i-1) == text2.charAt(j-1)) {
                    d[i][j] = d[i-1][j-1] + 1;
                } else {
                    d[i][j] = Math.max(d[i-1][j], d[i][j-1]);
                }
            }
        }

        return d[n][m];
    }
}
```