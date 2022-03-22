# 1. 설명
- 정렬된 배열에서 타켓이 포함된 인덱스를 모두 구하세요.


[문제 링크](https://leetcode.com/problems/find-target-indices-after-sorting-array/)

# 2. 코드
### 1) python
```python
class Solution:
    def targetIndices(self, nums: List[int], target: int) -> List[int]:
        # 1. sort
        nums.sort()
        n = len(nums)
        res = [x for x in range(n)]

        # 2. lower_bound
        def lower_bound(t):
            s, e = 0, n
            while s < e:
                mid = s + (e - s) // 2
                if nums[mid] < t:
                    s = mid + 1
                else:
                    e = mid
            return e

        # 3. upper_bound
        def upper_bound(t):
            s, e = 0, n
            while s < e:
                mid = s + (e - s) // 2
                if nums[mid] <= t:
                    s = mid + 1
                else:
                    e = mid
            return e

        # 4. check
        l, r = lower_bound(target), upper_bound(target) - 1
        if l <= r:
            res = res[l:r+1]
        else:
            res = []

        return res
```

### 2) java
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

class Solution {
    public List<Integer> targetIndices(int[] nums, int target) {
        // 1. init
        int n = nums.length;
        List<Integer> res = new ArrayList<>();
        nums = Arrays.stream(nums).boxed().sorted().mapToInt(i -> i).toArray();

        // 2, lowerBound, upperBound
        int l = lowerBound(0, n, nums, target);
        int r = upperBound(0, n, nums, target);

        if(l <= r) for(int i=l; i<r; i++) res.add(i);

        return res;
    }

    public int lowerBound(int start, int end, int[] nums, int target) {
        while(start < end) {
            int mid = start + (end - start) / 2;
            if(nums[mid] < target) start = mid + 1;
            else end = mid;
        }
        return end;
    }

    public int upperBound(int start, int end, int[] nums, int target) {
        while(start < end) {
            int mid = start + (end - start) / 2;
            if(nums[mid] <= target) start = mid + 1;
            else end = mid;
        }
        return end;
    }
}
```

### 3) JavaScript
```js
const targetIndices = function(nums, target) {
    // 1. init
    nums.sort((a, b) => a - b)
    const n = nums.length
    const base = Array.from(Array(n).keys())
    let res = []

    // 2. lowerBound
    const lowerBound = (target) => {
        let l = 0
        let r = n

        while(l<r) {
            const mid = l + Math.floor((r-l) / 2)
            if(nums[mid] < target) l = mid + 1
            else r = mid
        }
        return r
    }

    // 3. upperbound
    const upperBound = (target) => {
        let l = 0
        let r = n

        while(l<r) {
            const mid = l + Math.floor((r-l) / 2)
            if(nums[mid] <= target) l = mid + 1
            else r = mid
        }
        return r
    }

    const l = lowerBound(target)
    const r = upperBound(target)
    if(l <= r) res = base.slice(l, r)

    return res
};
```