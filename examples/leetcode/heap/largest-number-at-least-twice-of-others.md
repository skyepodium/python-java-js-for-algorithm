# 1. 설명
- 2번째 큰 수의 2배가 제일 큰 수보다 작거나 같은지 여부를 반환하세요


[문제 링크](https://leetcode.com/problems/largest-number-at-least-twice-of-others/)

# 2. 코드
### 1) Python
```python
class Solution:
    def dominantIndex(self, nums: List[int]) -> int:
        # 1. exception
        if len(nums) < 2: return 0

        # 2. init
        pq = []

        # 3. loop
        for idx, val in enumerate(nums):
            heappush(pq, (-val, idx))

        first, idx = heappop(pq)
        second, _ = heappop(pq)
        first, second = -first, -second

        return idx if first >= second * 2 else -1
```

### 2) Java
```java
class Solution {
    public int dominantIndex(int[] nums) {
        // 1. exception
        if(nums.length < 2) return 0;

        // 2. init
        PriorityQueue<Info> pq = new PriorityQueue<>((a, b) -> b.val - a.val);

        IntStream.range(0, nums.length).forEach(x -> pq.add(new Info(nums[x], x)));

        Info first = pq.poll();
        Info second = pq.poll();

        return first.val >= 2 * second.val ? first.idx : -1;
    }
}

class Info {
    public int val;
    public int idx;

    public Info(int val, int idx) {
        this.val = val;
        this.idx = idx;
    }
}
```

### 3) JavaScript
```js
const dominantIndex = (nums) => {
    // 1. exception
    if(nums.length < 2) return 0

    // 2. sort
    const l = nums.map((val, idx) => [val, idx])
        .sort((a, b) => b[0] - a[0])

    const first = l[0]
    const second = l[1]

    return first[0] >= second[0] * 2 ? first[1] : -1
};
```