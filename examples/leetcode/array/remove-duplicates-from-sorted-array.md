# 1. 설명
- 중복을 제거하세요.



[문제 링크](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

# 2. 코드
### 1) python
```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        count = 0
        n = len(nums)

        for i in range(1, n):
            if nums[i] == nums[i - 1]:
                count += 1
            else:
                nums[i - count] = nums[i]

        return n - count
```

### 2) java
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int cnt = 0;
        int n = nums.length;

        for(int i=1; i<n; i++) {
            if(nums[i] == nums[i-1]) cnt++;
            else nums[i-cnt] = nums[i];
        }
        return n - cnt;
    }
}
```