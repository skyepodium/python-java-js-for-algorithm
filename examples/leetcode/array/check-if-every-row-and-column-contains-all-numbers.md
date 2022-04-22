# 1. 설명
- 세로, 가로 모두 1~n의 원소가 포함되어있는지 여부를 반환하세요



[문제 링크](https://leetcode.com/problems/check-if-every-row-and-column-contains-all-numbers/)

# 2. 코드
### 1) Python
```python
class Solution:
    def checkValid(self, matrix: List[List[int]]) -> bool:
        # 1. init
        n = len(matrix)

        # 2. loop
        for a in matrix:
            s = set()
            for b in a:
                if b < 1 or b > n: return False
                if b in s: return False
                s.add(b)

        for j in range(n):
            s = set()
            for i in range(n):
                b = matrix[i][j]
                if b < 1 or b > n: return False
                if b in s: return False
                s.add(b)

        return True
```

### 2) Java
```java
class Solution {
    public boolean checkValid(int[][] matrix) {
        // 1. init
        int n = matrix.length;

        // 2. loop
        for(int i=0; i<n; i++) {
            Set<Integer> s = new HashSet<>();
            for(int j=0; j<n; j++) {
                int cur = matrix[i][j];

                if(cur < 1 || cur > n) return false;
                if(s.contains(cur)) return false;
                s.add(cur);
            }
        }

        for(int j=0; j<n; j++) {
            Set<Integer> s = new HashSet<>();
            for(int i=0; i<n; i++) {
                int cur = matrix[i][j];

                if(cur < 1 || cur > n) return false;
                if(s.contains(cur)) return false;
                s.add(cur);
            }
        }

        return true;
    }
}
```

### 3) JavaScript
```js
const checkValid = (matrix) => {
    // 1. init
    const n = matrix.length

    // 2. loop
    for(let i=0; i<n; i++) {
        const s = new Set()
        for(let j=0; j<n; j++) {
            const cur = matrix[i][j]

            if(cur < 1 || cur > n) return false
            if(s.has(cur)) return false
            s.add(cur)
        }
    }

    for(let j=0; j<n; j++) {
        const s = new Set()
        for(let i=0; i<n; i++) {
            const cur = matrix[i][j]

            if(cur < 1 || cur > n) return false
            if(s.has(cur)) return false
            s.add(cur)
        }
    }

    return true
};
```