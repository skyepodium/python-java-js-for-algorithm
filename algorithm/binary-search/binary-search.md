[leetcode - binary-search](https://leetcode.com/problems/binary-search/) - 이진탐색

# 이진 탐색 버그
바이너리 서치에서 mid 인덱스를 계산할 때 버그가 발생할 수 있습니다.

다음과 같이 두계를 합산해서 2로 나누는 경우 합산한 값이 int 범위를 넘어갈 수 있습니다.
```c
int mid = (start + end) / 2;
```

두 수의 차를 2로 나눈 값을 start에 더해줘서 mid 인덱스를 계산합니다.
```c
int mid = start + (end - start) / 2;
```

파이썬은 임의 정밀도 정수형을 지원하기 때문에 적용되지 않습니다.

# 1. python
## 1) loop
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
## 2) recursive
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:

        def binary_search(s, e, target):
            if s > e:
                return -1

            mid = s + (e - s) // 2
            if nums[mid] < target:
                return binary_search(mid + 1, e, target)
            elif nums[mid] > target:
                return binary_search(s, mid - 1, target)
            else:
                return mid

        return binary_search(0, len(nums) - 1, target)
```

# 2. java
## 1) loop
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
## 2) recursive
```java
class Solution {
    public int search(int[] nums, int target) {

        return binarySearch(0, nums.length - 1, nums, target);
    }

    public int binarySearch(int s, int e, int[] nums, int target) {
        // exception
        if(s > e) return -1;

        int mid = s + (e-s) / 2;

        if(nums[mid] < target) {
            return binarySearch(mid+1, e, nums, target);
        }
        else if(nums[mid] > target) {
            return binarySearch(s, mid-1, nums, target);
        }
        else {
            return mid;
        }
    }
}
```