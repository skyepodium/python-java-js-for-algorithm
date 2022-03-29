# 1. 설명
정렬했을 때 k번째로 큰 수 

[문제 링크](https://leetcode.com/problems/kth-largest-element-in-an-array/)

# 2. 코드
### 1) python
```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        return sorted(nums, reverse=True)[k-1]
```

### 2) java
```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
        return Arrays.stream(nums)
                .sorted()
                .toArray()[nums.length - k - 1];
    }
}
```

### 3) JavaScript
```js
const findKthLargest = (nums, k) => {
    return nums.sort((a, b) => b-a)[k-1]
};
```