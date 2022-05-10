# 1. 설명
- nums[i] 보다 작은 숫자의 개수를 구하세요


[문제 링크](https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/)

# 참고
O(N)에 풀어봅시다.

# 2. 코드
### 1) Python
```python
from typing import List

class Solution:
    def smallerNumbersThanCurrent(self, nums: List[int]) -> List[int]:
        # 1. init
        max_int = 101
        c = [0 for _ in range(max_int)]
        d = [0 for _ in range(max_int)]
        res = []

        # 2. loop
        for num in nums:
            c[num] += 1

        prev = 0
        for i in range(max_int):
            if c[i] != 0:
                d[i], prev = prev, c[i] + prev

        for num in nums:
            res.append(d[num])

        return res

```

### 2) Java
```java
class Solution {
    public int[] smallerNumbersThanCurrent(int[] nums) {
        // 1. init
        int maxInt = 101;
        int[] c = new int[maxInt];
        int[] d = new int[maxInt];
        int n = nums.length;
        int[] res = new int[n];

        // 2. loop
        for(int num: nums) {
            c[num]++;
        }

        int prev = 0;
        for(int i=0; i<maxInt; i++) {
            if(c[i] == 0) continue;
            d[i] = prev;
            prev += c[i];
        }

        for(int i=0; i<n; i++) {
            int num = nums[i];
            res[i] = d[num];
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const smallerNumbersThanCurrent = (nums) => {
    // 1. init
    const maxInt = 101
    const c = Array.from(new Array(maxInt).fill(0))
    const d = Array.from(new Array(maxInt).fill(0))

    // 2. loop
    nums.forEach(num => c[num]++)

    let prev = 0
    for(let i=0; i<maxInt; i++) {
        if(c[i] === 0) continue

        d[i] = prev
        prev += c[i]
    }

    return nums.map(num => d[num])
};
```

### 4) TypeScript
```ts
const smallerNumbersThanCurrent = (nums: number[]): number[] => {
    // 1. init
    const maxInt:number = 101
    const c:number[] = Array.from(new Array(maxInt).fill(0))
    const d:number[] = Array.from(new Array(maxInt).fill(0))

    // 2. loop
    nums.forEach(num => c[num]++)

    let prev:number = 0
    for(let i=0; i<maxInt; i++) {
        if(c[i] === 0) continue

        d[i] = prev
        prev += c[i]
    }

    return nums.map(num => d[num])
};
```