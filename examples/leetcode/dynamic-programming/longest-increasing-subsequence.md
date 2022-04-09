# 1. 설명
- 가장 긴 증가하는 부분수열의 길이를 구하세요

[문제 링크](https://leetcode.com/problems/longest-increasing-subsequence/)

# 2. 코드
### 1) Python
```python
 class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        # 1. init
        n = len(nums)
        d = [1 for _ in range(n)]

        # 2. loop
        for i in range(n):
            for j in range(i):
                if nums[j] < nums[i] and d[j] + 1 > d[i]:
                    d[i] = d[j] + 1

        return max(d)
```

### 2) Java
```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        // 1. init
        int n = nums.length;
        int[] d = new int[n];
        for(int i=0; i<n; i++) d[i] = 1;

        // 2. loop
        for(int i=0; i<n; i++) {
            for(int j=0; j<i; j++) {
                if(nums[i] > nums[j] && d[j] + 1 > d[i]){
                    d[i] = d[j] + 1;
                }
            }
        }

        return Arrays.stream(d).max().getAsInt();
    }
}
```

### JavaScript
```js
const lengthOfLIS = (nums) => {
    // 1. init
    const n = nums.length;
    const d = Array.from(Array(n)).fill(1)

    // 2. loop
    for(let i=0; i<n; i++) {
        for(let j=0; j<i; j++) {
            if(nums[i] > nums[j] && d[j] + 1 > d[i]) {
                d[i] = d[j] + 1
            }
        }
    }

    return Math.max(...d)
};
```