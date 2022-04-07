# 1. 설명
- 배열을 2n개의 pair로 나눌 수 있는지를 반환하세요



[문제 링크](https://leetcode.com/problems/divide-array-into-equal-pairs/)

# 2. 코드
### 1) Python
```python
class Solution:
    def divideArray(self, nums: List[int]) -> bool:
        return len([x for x in Counter(nums).values() if x % 2 != 0]) == 0
```

### 2) Java
```java
class Solution {
    public boolean divideArray(int[] nums) {
        Map<Integer, Integer> m = new HashMap<>();

        Arrays.stream(nums).forEach(x -> {
            m.put(x, m.getOrDefault(x, 0) + 1);
        });

        return m.values().stream()
                .filter(x -> x % 2 != 0)
                .collect(Collectors.toList())
                .size() == 0;
    }
}
```

### 3) JavaScript
```js
const divideArray = (nums) => {
    const m = new Map()

    nums.forEach(x => {
        if(m.has(x)) m.set(x, m.get(x) + 1)
        else m.set(x, 1)
    })

    return [...m.values()].filter(x => x % 2 !== 0).length === 0
};
```