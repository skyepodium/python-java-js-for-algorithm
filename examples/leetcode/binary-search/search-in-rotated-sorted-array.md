# 1. 설명
- 오름차순으로 정렬된 수열이 몇칸 pivot 되어있습니다.

- log(N) 만에 target의 인덱스를 반환하세요.

[문제 링크](https://leetcode.com/problems/search-in-rotated-sorted-array/submissions/)

# 2. 코드
### 1) python
```python
class Solution:
    def search(self, nums: list[int], target: int) -> int:

        # 1. find min idx
        def min_idx(l, r):
            while l < r:
                mid = l + (r-l) // 2

                if nums[mid] > nums[r]:
                    l = mid + 1
                else:
                    r = mid

            return l

        pivot_idx = min_idx(0, len(nums) - 1)

        # 2. get_origin_idx
        def get_origin_idx(cur_idx):
            if cur_idx + pivot_idx >= len(nums):
                origin = cur_idx + pivot_idx - len(nums)
            else:
                origin = cur_idx + pivot_idx
            return origin

        # 3. binary_search
        def binary_search(l, r):
            while l <= r:
                mid = l + (r-l) // 2
                origin_mid_idx = get_origin_idx(mid)
                if nums[origin_mid_idx] < target:
                    l = mid + 1
                elif nums[origin_mid_idx] > target:
                    r = mid - 1
                else:
                    return origin_mid_idx

            return -1

        return binary_search(0, len(nums) - 1)
```

### 2) java
```java
class Solution {

    int size, pivotIdx;
    public int search(int[] nums, int target) {
        // 0. init
        size = nums.length;

        // 1. find min idx
        pivotIdx = findMinIdx(0, nums.length-1, nums);

        return binarySearch(0, size - 1, nums, target);
    }

    public int findMinIdx(int l, int r, int[] nums){
        while(l < r) {
            int mid = l + (r-l) / 2;

            if(nums[mid] > nums[r]) {
                l = mid + 1;
            }
            else {
                r = mid;
            }
        }
        return l;
    }

    public int getOriginIdx(int curIdx) {
        if (curIdx + pivotIdx >= size) {
            return curIdx + pivotIdx - size;
        }
        else {
            return curIdx + pivotIdx;
        }
    }

    public int binarySearch(int l, int r, int[] nums, int target) {
        while(l <= r) {
            int mid = l + (r-l) / 2;
            int originMidIdx = getOriginIdx(mid);
            if(nums[originMidIdx] < target) {
                l = mid + 1;
            }
            else if(nums[originMidIdx] > target){
                r = mid - 1;
            }
            else {
                return originMidIdx;
            }
        }
        return -1;
    }
}
```