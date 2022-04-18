# 1. 설명
- 단조 증감, 감소 여부를 반환하세요


[문제 링크](https://leetcode.com/problems/monotonic-array/)


# 2. 코드
### 1) Python
```python
class Solution:
    def isMonotonic(self, nums: List[int]) -> bool:

        return nums == sorted(nums) or nums == sorted(nums, reverse=True)
```

### 2) Java
```java
class Solution {
    public boolean isMonotonic(int[] nums) {
        int[] increased = Arrays.stream(nums).sorted().toArray();
        int[] decreased = Arrays.stream(nums).boxed()
                                .sorted((a, b) -> b-a)
                                .mapToInt(x->x)
                                .toArray();

        boolean isIncreased = true;
        boolean isDecreased = true;
        for(int i=0; i<nums.length; i++) {
            if(nums[i] != increased[i]) isIncreased = false;
            if(nums[i] != decreased[i]) isDecreased = false;
        }

        return isIncreased || isDecreased;
    }
}
```

### 3) JavaScript
```js
const isMonotonic = (nums) => {
    const base = [...nums]
    const increased = [...base.sort((a, b) => a - b)]
    const decreased = [...base.sort((a, b) => b - a)]

    let isIncreased = true
    let isDecreased = true
    for(let i=0; i<nums.length; i++) {
        if(nums[i] !== increased[i]) isIncreased = false
        if(nums[i] !== decreased[i]) isDecreased = false
    }

    return isIncreased || isDecreased
};
```