# 1. 설명
- 중복 번호를 구하세요


[문제 링크](https://leetcode.com/problems/find-the-duplicate-number/)

# 2. 코드
### 1) python
```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        return Counter(nums).most_common()[0][0]
```

### 2) java
```java
class Solution {
    public int findDuplicate(int[] nums) {
        Set<Integer> s = new HashSet<>();

        for(int num: nums) {
            if(s.contains(num)) return num;

            s.add(num);
        }
        return -1;
    }
}
```

### 3) JavaScript
```js
const findDuplicate = (nums) => {
    const s = new Set()

    for(const num of nums) {
        if(s.has(num)) return num

        s.add(num)
    }
    return  - 1
};
```