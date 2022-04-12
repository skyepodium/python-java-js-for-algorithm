# 1. 설명
- 다른 수보다 작거나, 큰 수의 개수를 구하세요



[문제 링크](https://leetcode.com/problems/count-elements-with-strictly-smaller-and-greater-elements/)

# 2. 코드
### 1) Python
```python
class Solution:
    def countElements(self, nums: List[int]) -> int:
        min_val = min(nums)
        max_val = max(nums)
        
        res = 0
        for a in nums:
            if min_val < a < max_val: res += 1
                
        return res
```

### 2) Java
```java
class Solution {
    public int countElements(int[] nums) {
        int maxVal = Arrays.stream(nums).max().getAsInt();
        int minVal = Arrays.stream(nums).min().getAsInt();
        int res = 0;

        for(int num: nums) {
            if(num > minVal && num < maxVal) res++;
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const countElements = (nums) => {
    const maxVal = Math.max(...nums)
    const minVal = Math.min(...nums)
    let res = 0

    nums.forEach(x => {
        if(minVal < x && x < maxVal) res++
    })

    return res
};
```