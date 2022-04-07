# 1. 설명
- 가장 마지막에 남은 돌을 구하세요


[문제 링크](https://leetcode.com/problems/last-stone-weight/)

# 2. 코드
### 1) python
```python
class Solution:
    def lastStoneWeight(self, stones: List[int]) -> int:
        # 1. init
        pq = []
        for s in stones:
            heappush(pq, -s)

        # 2. loop
        while len(pq) >= 2:
            a = heappop(pq)
            b = heappop(pq)

            res = 0 if a == b else -abs(a - b)
            heappush(pq, res)

        return -pq[0]
```

### 2) java
```java
class Solution {
    public int lastStoneWeight(int[] stones) {
        // 1. init
        PriorityQueue<Integer> pq = new PriorityQueue<>((a, b) -> b-a);
        Arrays.stream(stones).forEach(pq::add);

        // 2. loop
        while(pq.size() >= 2) {
            int a = pq.poll();
            int b = pq.poll();

            int res = a == b ? 0 : Math.abs(a - b);
            pq.add(res);
        }

        return pq.peek();
    }
}
```

### 3) JavaScript
```js
const lastStoneWeight = (stones) => {
    // 1. loop
    while(stones.length >= 2) {
        stones.sort((a, b) => b-a)

        const a = stones.shift()
        const b = stones.shift()

        stones.push(a===b ? 0 : Math.abs(a-b))
    }

    return stones[0]
};
```