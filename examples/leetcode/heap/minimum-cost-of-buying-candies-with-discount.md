# 1. 설명
- 캔디 구매 최소비용을 구하세요


[문제 링크](https://leetcode.com/problems/minimum-cost-of-buying-candies-with-discount/)

# 2. 코드
### 1) python
```python
class Solution:
    def minimumCost(self, cost: List[int]) -> int:
        # 1. init
        pq = []
        res = 0
        
        for c in cost:
            heappush(pq, -c)
 
        # 2. loop
        while pq:
            if len(pq) >= 2:
                a = -heappop(pq)
                b = -heappop(pq)
                res += a + b
                
                if len(pq) >= 1: heappop(pq)
            else:
                break
                
        return res - sum(pq)
```

### 2) Java
```java
class Solution {
    public int minimumCost(int[] cost) {
        // 1. init
        PriorityQueue<Integer> pq = new PriorityQueue<>((a, b) -> b-a);
        int res = 0;

        Arrays.stream(cost).forEach(pq::add);

        // 2. loop
        while(!pq.isEmpty()) {
            if(pq.size() >= 2) {
                int a = pq.poll();
                int b = pq.poll();
                res += a + b;

                if(pq.size() >= 1) pq.poll();
            }
            else break;
        }

        while(!pq.isEmpty()) res += pq.poll();

        return res;
    }
}
```

### 3) JavaScript
```js
const minimumCost = (cost) => {
    let res = 0

    while(cost.length >= 1) {
        cost.sort((a, b) => a - b)
        if(cost.length >= 2) {
            const a = cost.pop()
            const b = cost.pop()

            res += a + b
            if(cost.length >= 1) cost.pop()
        }
        else break
    }

    while(cost.length >= 1) res += cost.pop()

    return res
};
```