# 1. 설명
- index 위치에 num을 넣으세요


[문제 링크](https://leetcode.com/problems/create-target-array-in-the-given-order/)

# 2. 코드
### 1) Python
```python
class Solution:
    def createTargetArray(self, nums: List[int], index: List[int]) -> List[int]:
        # 1. init
        res = []

        # 2. loop
        for num, idx in zip(nums, index):
            res.insert(idx, num)

        return res
```

### 2) Java
```java
class Solution {
    public int[] createTargetArray(int[] nums, int[] index) {
        // 1. init
        List<Integer> res = new LinkedList<>();
        int n = nums.length;

        // 2. loop
        for(int i=0; i<n; i++) {
            res.add(index[i], nums[i]);
        }

        return res.stream().mapToInt(x -> x).toArray();
    }
}
```

### 3) JavaScript
```js
const createTargetArray = (nums, index) => {
    // 1. init
    let res = []
    const n = nums.length

    // 2. loop
    for(let i=0; i<n; i++) {
        const idx = index[i]
        const num = nums[i]

        res = res.slice(0, idx).concat([num]).concat(res.slice(idx))
    }

    return res
};
```