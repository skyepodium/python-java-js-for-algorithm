# 1. 설명
- 가로, 세로 오름차순 정렬된 2D 배열에서 target의 유무를 반환하세요.


[문제 링크](https://leetcode.com/problems/search-a-2d-matrix/)

# 비고
이진 탐색 문제이지만, 여러가지 방법이 있다.
생각을 넓게 하자

# 2. 코드
## 1) 이진 탐색
### 1) python
```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:

        # 1. init
        n = len(matrix)
        m = len(matrix[0])

        # 2. vertical_binary_search
        def vertical_binary_search(l, r):

            while l < r:
                mid = l + (r - l) // 2

                if matrix[mid][0] < target:
                    l = mid + 1
                else:
                    r = mid
            return r - 1 if matrix[r][0] > target else r

        v_idx = vertical_binary_search(0, n - 1)

        # 3. horizontal_binary_search
        def horizontal_binary_search(l, r, v_idx):
            while l <= r:
                mid = l + (r - l) // 2
                cur = matrix[v_idx][mid]
                if cur < target:
                    l = mid + 1
                elif cur > target:
                    r = mid - 1
                else:
                    return True
            return False

        return horizontal_binary_search(0, m - 1, v_idx)
```

### 2) java
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        // 1. init
        int n = matrix.length;
        int m = matrix[0].length;

        // 2. verticalBinarySearch
        int vIdx = verticalBinarySearch(0, n-1, matrix, target);

        if (vIdx < 0) return false;

        // 3. horizontalBinarySearch
        return horizontalBinarySearch(0, m-1, matrix, target, vIdx);
    }

    public boolean horizontalBinarySearch(int l, int r, int[][] matrix, int target, int vIdx) {
        while(l <= r) {
            int mid = l + (r-l) / 2;
            int cur = matrix[vIdx][mid];

            if(cur < target) {
                l = mid + 1;
            }
            else if(cur > target) {
                r = mid - 1;
            }
            else{
                return true;
            }
        }
        return false;
    }

    public int verticalBinarySearch(int l, int r, int[][] matrix, int target) {

        while (l < r) {
            int mid = l + (r-l) / 2;
            int cur = matrix[mid][0];

            if(cur < target) {
                l = mid + 1;
            }
            else {
                r = mid;
            }
        }
        return matrix[r][0] > target ? r - 1 : r;
    }
}
```

### 3) JavaScript
```js
const searchMatrix = (matrix, target) => {
    // 1. init
    const n = matrix.length
    const m = matrix[0].length

    const lowerBound = () => {
        let s = 0
        let e = n

        while(s < e) {
            const mid = s + ~~((e-s)/2)
            if(matrix[mid][0] < target) {
                s = mid + 1
            } else {
                e = mid
            }
        }
        return e
    }

    let lowerIdx = lowerBound()
    if(lowerIdx < 0) lowerIdx = 0
    if(lowerIdx >= n) lowerIdx = n-1
    if(matrix[lowerIdx][0] > target && lowerIdx > 0) lowerIdx--

    const binarySearch = (idx) => {
        let s = 0
        let e = m - 1

        while(s <= e) {
            const mid = s + ~~((e-s)/2)
            const cur = matrix[idx][mid]
            if(cur < target) {
                s = mid + 1
            }
            else if(cur === target) return mid
            else {
                e = mid - 1
            }
        }
        return -1
    }

    return binarySearch(lowerIdx) !== -1
};
```


## 2) 반복문
### 1) python
```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        # 1. exception
        if not matrix:
            return -1
        
        # 2. init
        i = 0
        j = len(matrix[0]) - 1
        n = len(matrix)
        m = len(matrix[0])
        
        # 3. loop
        while i < n and j >=0:
            cur = matrix[i][j]
            
            if cur > target:
                j -= 1
            elif cur < target:
                i += 1
            else:
                return True
            
        return False
```

### 2) java
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        // 1. init
        int n = matrix.length - 1;
        int m = matrix[0].length - 1;
        int i = 0;
        int j = m;

        // 2. loop
        while (i<=n && j>=0) {
            int cur = matrix[i][j];

            if(cur > target) {
                j--;
            }
            else if (cur < target) {
                i++;
            }
            else {
                return true;
            }
        }
        return false;
    }
}
```

## 3) python any
```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        return any(target in x for x in matrix)
```