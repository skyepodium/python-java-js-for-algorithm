# 1. 설명
- original이 nums에 포함되어 있는 개수만큼 * 2를 하세요



[문제 링크](https://leetcode.com/problems/keep-multiplying-found-values-by-two/)

# 2. 코드
### 1) Python
```python
class Solution:
    def findFinalValue(self, nums: List[int], original: int) -> int:
        s = set(nums)

        while original in s:
            original *= 2

        return original
```

### 2) Java
```java
class Solution {
    public int findFinalValue(int[] nums, int original) {
        Set<Integer> s = new HashSet<>(Arrays.stream(nums).boxed().collect(Collectors.toList()));

        while(s.contains(original)) original *= 2;

        return original;
    }
}
```

### 3) JavaScript
```js
const findFinalValue = (nums, original) => {
    const s = new Set(nums)

    while(s.has(original)) original *= 2

    return original
};
```