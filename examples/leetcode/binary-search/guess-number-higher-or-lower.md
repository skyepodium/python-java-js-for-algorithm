# 1. 설명
- 이진탐색

[문제 링크](https://leetcode.com/problems/guess-number-higher-or-lower/)

# 2. 코드
### 1) Python
```python
class Solution:
    def guessNumber(self, n: int) -> int:
        # 1. init
        s, e = 1, n
        
        # 2. binary search
        while s <= e:
            mid = s + (e - s) // 2
            val = guess(mid)
            
            if val == 1: s = mid + 1
            elif val == 0: return mid
            else: e = mid - 1
            
        return -1
```

### 2) Java
```java
public class Solution extends GuessGame {
    public int guessNumber(int n) {
        // 1. init
        int s = 1;
        int e = n;
        
        // 2. binarySearch
        while(s <= e) {
            int mid = s + (e - s) / 2;
            int val = guess(mid);
            if(val == 1) s = mid + 1;
            else if(val == 0) return mid;
            else e = mid - 1;
        }
        
        return -1;
    }
}
```

### 3) JavaScript
```js
const guessNumber = (n) => {
    // 1. init
    let s = 1
    let e = n
    
    // 2. binarySearch
    while(s <= e) {
        const mid = s + ~~((e - s) / 2)
        const val = guess(mid)
        
        if(val === 1) s = mid + 1
        else if(val === 0) return mid
        else e = mid - 1
    }
    
    return -1
};
```