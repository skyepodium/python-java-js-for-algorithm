# 1. 설명
- K 번째로 큰 수를 구하세요


[문제 링크](https://leetcode.com/problems/kth-largest-element-in-a-stream/)

# 2. 코드
### 1) Python
```python
class KthLargest:
    def __init__(self, k: int, nums: List[int]):
        self.k = k
        self.l = nums
        heapify(self.l)
        while len(self.l) > self.k:
            heappop(self.l)

    def add(self, val: int) -> int:
        heappush(self.l, val)

        if len(self.l) > self.k:
            heappop(self.l)

        return self.l[0]
```

### 2) Java
```java
class KthLargest {
    private PriorityQueue<Integer> pq;
    private int k;

    public KthLargest(int k, int[] nums) {
        this.k = k;

        this.pq = new PriorityQueue<>(Comparator.comparingInt(a -> a));
        Arrays.stream(nums).forEach(x -> pq.add(x));

        while(pq.size() > k) pq.poll();
    }

    public int add(int val) {
        this.pq.add(val);

        while(pq.size() > k) pq.poll();

        return pq.peek();
    }
}
```

### 3) JavaScript
```js
const KthLargest = function(k, nums) {
    this.k = k
    this.nums = nums
    this.nums.sort((a, b) => b-a)

    while(this.nums.length > this.k) {
        this.nums.pop()
    }
};


KthLargest.prototype.add = function(val) {
    this.nums.push(val)
    this.nums.sort((a, b) => b-a)

    while(this.nums.length > this.k) {
        this.nums.pop()
    }

    return this.nums[this.nums.length - 1]
};
```

### 4) Kotlin
```kt
class KthLargest(k: Int, nums: IntArray) {

    private val pq: PriorityQueue<Int> = PriorityQueue(k) { a, b -> a-b }
    private val k = k

    init {
        for(element in nums) pq.add(element)

        while(pq.size > k) pq.poll()
    }

    fun add(a: Int): Int {
        pq.add(a)

        while(pq.size > k) pq.poll()

        return pq.peek()
    }
}
```

### 5) TypeScript
```ts
class KthLargest {
    
    k: number
    nums: Array<number>
    constructor(k: number, nums: number[]) {
        this.k = k
        this.nums = nums
        this.nums.sort((a, b) => b-a)

        while(this.nums.length > this.k) this.nums.pop()
    }

    add(val: number): number {
        this.nums.push(val)
        this.nums.sort((a, b) => b-a)

        while(this.nums.length > this.k) this.nums.pop()

        return this.nums[this.nums.length - 1]
    }
}
```