# 1. 설명
- 두 수의 합이 k가 되는 경우를 구하세요


[문제 링크](https://leetcode.com/problems/max-number-of-k-sum-pairs/)

# 참고
사실 이런 문제 보면, 거의 본능적으로 투포인터로 구현하는데 투포인터는 정렬이 필요하기 때문에 O(nlogn)이 걸린다.

가끔씩 잊지만, Hash를 사용하면 O(n)에 풀 수 있다.

# 2. 코드
### 1) Python
```python
from collections import Counter
from typing import List

"""
시간 복잡도: O(n)
공간 복잡도: O(1)
사용한 알고리즘: 반복문
사용한 자료구조: 해시맵
"""


class Solution:
    def maxOperations(self, nums: List[int], k: int) -> int:
        # 1. init
        c = Counter(nums)
        res = 0

        # 2. loop
        for num in nums:
            remain = k - num
            if num == remain and c[remain] <= 1: continue
            if c[remain] < 1 or c[num] < 1: continue

            res += 1
            c[remain] -= 1
            c[num] -= 1

        return res

```

### 2) Java
```java
import java.util.Arrays;
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int maxOperations(int[] nums, int k) {
        // 1. init
        Map<Integer, Integer> m = new HashMap<>();
        Arrays.stream(nums).forEach(x -> m.put(x, m.getOrDefault(x, 0) + 1));
        int n = nums.length;
        int res = 0;

        // 2. loop
        for(int num: nums) {
            int remain = k - num;
            if(num == remain && m.getOrDefault(remain, 0) <= 1) continue;
            if(m.getOrDefault(remain, 0) < 1 || m.getOrDefault(num, 0) < 1) continue;

            res++;
            m.put(remain, m.get(remain) - 1);
            m.put(num, m.get(num) - 1);
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const maxOperations = (nums, k) => {
    // 1. init
    let res = 0
    const m = new Map()
    nums.forEach(num => {
        m.has(num) ? m.set(num, m.get(num) + 1) : m.set(num, 1)
    })

    // 2. loop
    for(const num of nums) {
        const remain = k - num

        if(!m.has(remain)) continue
        if(num === remain && m.get(remain) <= 1) continue
        if(m.get(remain) < 1 || m.get(num) < 1) continue

        res++
        m.set(remain, m.get(remain) - 1)
        m.set(num, m.get(num) - 1)
    }

    return res
};
```

### 4) TypeScript
```ts
const maxOperations = (nums: number[], k: number): number => {
    // 1. init
    let res:number = 0
    const m = new Map<number, number>();
    nums.forEach(num => {
        m.has(num) ? m.set(num, m.get(num) + 1) : m.set(num, 1)
    })

    // 2. loop
    for(const num of nums) {
        const remain:number = k - num

        if(!m.has(remain)) continue
        if(num === remain && m.get(remain) <= 1) continue
        if(m.get(remain) < 1 || m.get(num) < 1) continue

        res++
        m.set(remain, m.get(remain) - 1)
        m.set(num, m.get(num) - 1)
    }

    return res
};
```