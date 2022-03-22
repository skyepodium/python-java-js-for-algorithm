# 1. 설명
- 증가하는 부분배열의 합중 가장큰 값을 반환하세요.


[문제 링크](https://leetcode.com/problems/maximum-ascending-subarray-sum/)


# 2. 코드
### 1) python
```python
class Solution:
    def maxAscendingSum(self, nums: List[int]) -> int:
        # 1. init
        res = 0
        cur = 0
        prev = -1

        # 2. loop
        for num in nums:
            if num > prev:cur += num
            else:
                cur = num
            prev = num

            res = max(res, cur)

        return res
```

### 2) java
```java
class Solution {
    public int maxAscendingSum(int[] nums) {
        // 1. init
        int res = 0;
        int cur = 0;
        int prev = -1;
        
        // 2. loop
        for(int i=0; i<nums.length; i++) {
            int num = nums[i];
            if(num > prev) {
                cur += num;
            }else{
                cur = num;
            }
            
            prev = num;
            res = Math.max(res, cur);
        }
        
        return res;
    }
}
```

### 3) JavaScript
```js
const maxAscendingSum = (nums) => {
    // 1. init
    let res = 0
    let prev = 0
    let cur = 0
    
    // 2. loop
    nums.forEach(x => {
        if(x > prev) {
            cur +=  x
        } 
        else {
            cur = x
        }
        prev = x
        
        res = Math.max(res, cur)
    })
    
    return res
};
```