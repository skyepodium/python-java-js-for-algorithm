# 1. 설명
- 오름차순으로 정렬된 nums 배열에서 target과 같은 값을 가지는 값의 인덱스를 반환하세요.


[문제 링크](https://leetcode.com/problems/binary-search/)

# 2. 코드
### 1) python
```python
class Solution:
    def search(self, nums: list[int], target: int) -> int:

        # 1. binary_search
        def binary_search(l, r):
            while l <= r:
                mid = l + (r - l) // 2

                if nums[mid] < target:
                    l = mid + 1
                elif nums[mid] > target:
                    r = mid - 1
                else:
                    return mid
            return -1

        return binary_search(0, len(nums) - 1)
```

### 2) java
```java
class Solution {
    public int search(int[] nums, int target) {
        int l = 0;
        int r = nums.length - 1;

        return binarySearch(l,r, nums, target);
    }

    public int binarySearch(int l, int r, int[] nums, int target) {
        while(l <= r) {
            int mid = l + (r-l) / 2;

            if(nums[mid] < target) {
                l = mid + 1;
            }
            else if(nums[mid] > target) {
                r = mid - 1;
            }
            else {
                return mid;
            }
        }
        return -1;
    }
}
```