# 1. 설명
- 첫번째 불량 버전을 찾으세요


[문제 링크](https://leetcode.com/problems/first-bad-version/)

# 2. 코드
### 1) python
```python
class Solution:
    def firstBadVersion(self, n: int) -> int:
        # 1. init
        s, e = 0 , n
        
        # 2. lower bound
        while s < e:
            mid = s + (e - s) // 2
            if not isBadVersion(mid):
                s = mid + 1
            else:
                e = mid
                
        return e
```

### 2) Java
```java
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        // 1. init
        int s = 0, e = n;

        // 2. lower bound
        while(s < e) {
            int mid = s + (e - s) / 2;
            if(!isBadVersion(mid)) s = mid + 1;
            else e = mid;
        }
        return e;
    }
}
```

### 3) JavaScript
```js
const solution = (isBadVersion) => {
    return function(n) {
        let s = 0
        let e = n
        
        while(s < e) {
            const mid = s + ~~((e - s) / 2)
            if(!isBadVersion(mid)) s = mid + 1
            else e = mid
        }
        
        return e
    };
};
```