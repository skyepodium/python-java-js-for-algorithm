# 1. 설명
- 빈도수 오름차순 순, 빈도 같으면 숫자 내림차순 정렬


[문제 링크](https://leetcode.com/problems/sort-array-by-increasing-frequency/)

# 2. 코드
### 1) python
```python
class Solution:
    def frequencySort(self, nums: List[int]) -> List[int]:
        # 1. init
        res = []

        # 2. loop
        for key, val in sorted(Counter(nums).items(), key=lambda x: (x[1], -x[0])):
            res += [key] * val

        return res
```

### 2) Java
```java
class Solution {
    public int[] frequencySort(int[] nums) {
        // 1. init
        int[] res = new int[nums.length];
        AtomicInteger idx = new AtomicInteger();
        Map<Integer, Integer> c = new HashMap<>();

        // 2. loop
        Arrays.stream(nums).forEach(x -> c.put(x, c.getOrDefault(x, 0) + 1));
        c.entrySet().stream()
                .sorted((a, b) -> Objects.equals(a.getValue(), b.getValue()) ? b.getKey() - a.getKey() : a.getValue().compareTo(b.getValue()))
                .forEach(x -> {
                    for(int i=0; i<x.getValue(); i++) {
                        res[idx.getAndIncrement()] = x.getKey();
                    }
                });

        return res;
    }
}
```

### 3) JavaScript
```js
const frequencySort = (nums) => {
    // 1. init
    const m = new Map
    const res = []

    // 2. counter
    nums.forEach(x => {
        if(m.has(x)) m.set(x, m.get(x) + 1)
        else m.set(x, 1)
    })

    const sortedArr = [...m.entries()]
                .sort((a, b) => a[1] === b[1] ? b[0] - a[0] : a[1] - b[1])

    sortedArr.forEach(x => {
                    const [key, val] = x
                    for(let i=0; i<val; i++) res.push(key)
                })

    return res
};
```