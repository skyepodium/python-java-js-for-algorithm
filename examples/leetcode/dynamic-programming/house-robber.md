# 1. 설명
- 도둑은 바로 옆집에서 물건을 훔칠 수 없다.

- 도둑이 훔칠 수 있는 최대 값을 구하세요.


[문제 링크](https://leetcode.com/problems/house-robber/)

# 2. 코드
### 1) python
```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        # 0. exception        
        if len(nums) <= 2:
            return max(nums)

        # 1. init
        d = [x for x in nums]
        d[0] = nums[0]
        d[1] = max(nums[0], nums[1])

        # 2. tabulation
        for i in range(2, len(nums)):
            d[i] = max(d[i - 1], d[i - 2] + nums[i])

        return d[len(nums) - 1]
```

### 2) java
```java
class Solution {

    int[] d;
    int res = 0;
    int size = 0;
    public int rob(int[] nums) {
        // 1. init
        size = nums.length;
        d = new int[size];

        // 2. exception
        if(size <= 2) {
            return max(nums);
        }

        // 3. tabulation
        d[0] = nums[0];
        d[1] = max(nums[0], nums[1]);
        for(int i=2; i<size; i++) {
            d[i] = max(d[i-2] + nums[i], d[i-1]);
        }

        return d[size-1];
    }

    public int max(int[] arr) {
        res = 0;
        for(int num: arr) {
            res = max(res, num);
        }
        return res;
    }

    public int max(int a, int b){
        return a > b ? a : b;
    }
}
```