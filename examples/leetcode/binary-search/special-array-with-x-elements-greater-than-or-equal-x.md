# 1. 설명
- x 보다 크거나 같은 수가 x개가 나오는 x를 구하세요


[문제 링크](https://leetcode.com/problems/special-array-with-x-elements-greater-than-or-equal-x/)

# 2. 코드
### 1) Python
```python
from typing import List


class Solution:
    def specialArray(self, nums: List[int]) -> int:
        # 1. init
        max_val = max(nums)
        res = -1

        # 2. cal cnt
        def cal_cnt(mid):
            return sum([1 for x in nums if x >= mid])

        # 3. sort
        nums.sort()

        # 4. binary search
        s, e = 0, max_val
        while s <= e:
            mid = s + (e - s) // 2
            cnt = cal_cnt(mid)
            if cnt > mid:
                s = mid + 1
            elif cnt == mid:
                return mid
            else:
                e = mid - 1

        return res
```

### 2) Java
```java
import java.util.Arrays;

class Solution {
    public int specialArray(int[] nums) {
        // 1. init
        int maxVal = Arrays.stream(nums).max().orElse(0);
        int res = -1;

        // 2. binary search
        int s = 0, e = maxVal;
        while(s <= e) {
            int mid = s + (e - s) / 2;
            int cnt = calCnt(mid, nums);
            if(cnt > mid) {
                s = mid + 1;
            }
            else if(cnt == mid) {
                return mid;
            }
            else {
                e = mid - 1;
            }
        }

        return res;
    }

    public int calCnt(int mid, int[] nums) {
        int res = 0;
        for(int x: nums) {
            if(x >= mid) res++;
        }
        return res;
    }
}
```

### 3) JavaScript
```js
const specialArray = (nums) => {
    // 1. init
    const maxVal = Math.max(...nums)
    let res = -1

    // 2. calCnt
    const calCnt = mid => {
        let res = 0
        for(const x of nums) {
            if(x >= mid) res += 1
        }
        return res
    }

    // 3. binary search
    let s = 0, e = maxVal
    while(s <= e) {
        const mid = s + Math.trunc((e - s) / 2)
        const cnt = calCnt(mid)
        if(cnt > mid) {
            s = mid + 1
        }
        else if(cnt === mid) {
            return mid
        }
        else {
            e = mid - 1
        }
    }

    return res
};
```