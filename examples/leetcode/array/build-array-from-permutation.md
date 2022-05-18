# 1. 설명
- 규칙에 따라 배열을 반환하세요


[문제 링크](https://leetcode.com/problems/build-array-from-permutation/)

# 2. 코드
### 1) Python
```python
from typing import List

class Solution:
    def buildArray(self, nums: List[int]) -> List[int]:
        return [nums[num] for num in nums]
```

### 2) Java
```java
import java.util.Arrays;

class Solution {
    public int[] buildArray(int[] nums) {
        return Arrays.stream(nums).map(num -> nums[num]).toArray();
    }
}
```

### 3) JavaScript
```js
const buildArray = (nums) => {
    return nums.map(num => nums[num])
};
```

### 4) TypeScript
```ts
const buildArray = (nums: number[]): number[] => {
    return nums.map(num => nums[num])
};
```