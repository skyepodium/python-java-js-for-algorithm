# 1. 설명
- 없는 숫자를 반환하세요

[문제 링크](https://leetcode.com/problems/missing-number/)

# 2. 코드
### 1) python
```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        return (Counter([x for x in range(len(nums) + 1)]) - Counter(nums)).most_common()[0][0]

```

### 2) java
```java
class Solution {
    public int missingNumber(int[] nums) {
        Set<Integer> s = new HashSet<>();
        Arrays.stream(nums).forEach(s::add);

        for(int i=0; i<=nums.length; i++) {
            if(!s.contains(i)) return i;
        }
        return -1;
    }
}
```

### 3) JavaScript
```js
const missingNumber = (nums) => {
    const s = new Set(nums)

    for(let i=0; i<=nums.length; i++) {
        if(!s.has(i)) return i
    }
};

```