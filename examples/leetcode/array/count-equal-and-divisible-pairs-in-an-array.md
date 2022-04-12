# 1. 설명
- 

[문제 링크](https://leetcode.com/problems/count-equal-and-divisible-pairs-in-an-array/)

# 2. 코드
### 1) Python
```python
class Solution:
    def countPairs(self, nums: List[int], k: int) -> int:
        # 1. init
        n = len(nums)
        res = 0

        # 2. loop
        for i in range(n - 1):
            for j in range(i + 1, n):
                if nums[i] == nums[j] and (i * j) % k == 0: res += 1

        return res
```

### 2) Java
```java
class Solution {
    public int countPairs(int[] nums, int k) {
        // 1. init
        int res = 0;
        int n = nums.length;

        // 2. loop
        for(int i=0; i<n-1; i++){
            for(int j=i+1; j<n; j++) {
                if(nums[i] == nums[j] && (i*j) % k == 0) res++;
            }
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const countPairs = (nums, k) => {
    // 1. init
    let res = 0
    const n = nums.length

    // 2. loop
    for(let i=0; i<n-1; i++) {
        for(let j=i+1; j<n; j++) {
            if(nums[i] === nums[j] && (i*j) % k === 0) res++
        }
    }

    return res
};
```