# 1. 설명
- 오름차순으로 정렬된 nums 배열에서 target과 같은 값을 가지는 값의 인덱스를 반환하세요.


[문제 링크](https://leetcode.com/problems/binary-search/)

# 2. 코드
### 1) python
### loop
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
### recursive
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

### 2) java
### loop
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
### recursive
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

### 3) JavaScript
### loop
```js
const search = (nums, target) => {

    const binarySearch = (nums, target) => {
        let s = 0
        let e = nums.length - 1

        while(s <= e) {
            const mid = s + Math.floor((e - s) / 2)
            const cur = nums[mid]

            if(cur < target)  s = mid + 1
            else if(cur === target) return mid
            else e = mid - 1
        }

        return -1
    }

    return binarySearch(nums, target)
};
```

### recursive
```js
const search = (nums, target) => {

    const binarySearch = (s, e, nums, target) => {
        if(s > e) return -1

        const mid = s + ~~((e-s) / 2)
        const cur = nums[mid]

        if(cur < target) return binarySearch(mid+1, e, nums, target)
        else if(cur === target) return mid
        else return binarySearch(s, mid-1, nums, target)
    }

    return binarySearch(0, nums.length - 1, nums, target)
};
```

### 4) Kotlin
### loop
```kt
class Solution {
    fun search(nums: IntArray, target: Int): Int {
        var s = 0
        var e: Int = nums.size - 1

        while(s <= e) {
            val mid: Int = s + (e - s) / 2

            if(nums[mid] < target) s = mid + 1
            else if(nums[mid] == target) return mid
            else e = mid - 1
        }

        return -1
    }
}
```

### 2) recursive
```kt
class Solution {
    fun search(nums: IntArray, target: Int): Int {

        return binarySearch(nums, target, 0, nums.size - 1)
    }

    private fun binarySearch(nums: IntArray, target: Int, s: Int, e: Int): Int {
        if(s > e) return -1

        val mid: Int = s + (e - s) / 2

        return if(nums[mid] < target) binarySearch(nums, target, mid+1, e)
        else if(nums[mid] == target) mid
        else binarySearch(nums, target, s, mid - 1)
    }
}
```