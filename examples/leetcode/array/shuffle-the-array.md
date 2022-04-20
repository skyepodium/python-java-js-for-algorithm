# 1. 설명
- 배열 2개를 셔플하세요


[문제 링크](https://leetcode.com/problems/shuffle-the-array/)

# 2. 코드
### 1) Python
### flatmap - sum
```python
class Solution:
    def shuffle(self, nums: List[int], n: int) -> List[int]:
        
        return sum([[a, b] for a, b in zip(nums[:n], nums[n:])], [])
```
#### flatmap - 리스트 컴프리헨션
```python
class Solution:
    def shuffle(self, nums: List[int], n: int) -> List[int]:
        
        return [y for x in [[a, b] for a, b in zip(nums[:n], nums[n:])] for y in x]
```

### 2) Java
```java
class Solution {
    public int[] shuffle(int[] nums, int n) {
        // 1. init
        List<Integer> l = new ArrayList<>();

        // 2. loop
        for(int i=0; i<n; i++) {
            l.add(nums[i]);
            l.add(nums[i+n]);
        }

        return l.stream().mapToInt(x -> x).toArray();
    }
}
```

### 3) JavaScript
```js
const shuffle = (nums, n) => {
    function* zip(a, b) {
        const n = Math.min(a.length, b.length)

        for(let i=0; i<n; i++) {
            yield [a[i], b[i]]
        }
    }
    return [...zip(nums.slice(0, n), nums.slice(n))].flatMap(x => x)
};
```