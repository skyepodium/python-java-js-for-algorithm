# 1. 설명
- 유니크 원소의 합을 구하세요


[문제 링크](https://leetcode.com/problems/sum-of-unique-elements/)

# 2. 코드
### 1) python
```python
class Solution:
    def sumOfUnique(self, nums: List[int]) -> int:
        return sum([x for x, cnt in Counter(nums).items() if cnt == 1])
```

### 2) java
```java
class Solution {
    public int sumOfUnique(int[] nums) {
        Map<Integer, Integer> m = new HashMap<>();

        Arrays.stream(nums).forEach(x -> m.put(x, m.getOrDefault(x, 0) + 1));

        return m.entrySet().stream().filter(x -> x.getValue() == 1)
                .map(Map.Entry::getKey)
                .reduce(Integer::sum)
                .orElse(0);
    }
}
```

### 3) JavaScript
```js
const sumOfUnique = (nums) => {
    const m = new Map()

    nums.forEach(x => {
        if(m.has(x)) m.set(x, m.get(x) + 1)
        else m.set(x, 1)
    })

    return [...m.entries()].filter(x => x[1] === 1)
                            .map(x => x[0])
                            .reduce((prev, cur) => prev + cur, 0)
};
```