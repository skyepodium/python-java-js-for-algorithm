# 1. 설명
- 중복 여부를 반환하세요.

- 배열의 길이 1 <= n <= 10만



[문제 링크](https://leetcode.com/problems/contains-duplicate/)

# 2. 코드
### 1) python
```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(nums) != len(set(nums))
```

### 2) java
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> s = new HashSet<>();

        for(int x: nums) {
            if(!s.contains(x)) s.add(x);
            else return true;
        }

        return false;
    }
}
```

### 3) JavaScript
```js
const containsDuplicate = (nums) => {
    return new Set(nums).size !== nums.length
};
```

### 4) TypeScript
```ts
const containsDuplicate = (nums: number[]): boolean => {
    return new Set(nums).size !== nums.length
};
```