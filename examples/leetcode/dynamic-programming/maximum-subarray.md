# 1. 설명
- 배열에서 연속된 수들의 합의 최대값을 구하세요.


[문제 링크](https://leetcode.com/problems/maximum-subarray/)

# 2. 코드
### 1) python
```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        
        # 1. init
        d = [0 for _ in range(len(nums))]
        res = d[0] = nums[0]
        
        # 2. tabulation
        for i in range(1, len(nums)):
            d[i] = max(nums[i], d[i-1] + nums[i])
            res = max(res, d[i])
            
        return res
        
```

### 2) java
```java
class Solution {
    public int maxSubArray(int[] nums) {
        // 1. init
        int size = nums.length;
        int[] d = new int[size];
        int res = d[0] = nums[0];
        
        // 2. tabulation
        for(int i=1; i<size; i++) {
            d[i] = max(nums[i], d[i-1] + nums[i]);
            
            res = max(res, d[i]);
        }
        
        return res;
    }
    
    public int max(int a, int b) {
        return a > b ? a : b;
    }
}
```