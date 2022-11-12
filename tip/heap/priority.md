# 우선순위 큐

# 요약
- python - heapq
- java - PriorityQueue
- JavaScript- 빌트인 자료구조가 없다. 시간복잡도 이내면 정렬을 사용하고, 없으면 직접구현

### 1) 일반
코딩테스트에서 3가지 언어 모두 사용 가능한데 자바스크립트 힙이 필요하면 조금 의심해봐야한다.

### 2) 다익스트라
다익스트라 알고리즘의 경우 다음 문체처럼 우선순위큐 대신 일반 큐를 사용해도 시간안에 들어오도록 설계된다.   
[프로그래머스 - 경주로 건설](https://programmers.co.kr/learn/courses/30/lessons/67259)

[leetcode - path-with-minimum-effort](https://leetcode.com/problems/path-with-minimum-effort/)
### 1. python
- min heap (default)   
기본적으로 min heap이 제공됩니다. max heap이 필요한 경우 -를 붙여서 값을 넣어줍니다.

- top   
top은 메서드가 별도로 제공되지 않고, `heap[0]`을 사용하면 됩니다. 내부적으로 정렬되어있지 않아도 첫번째 요소는 우선순위를 충족합니다.

```python
from heapq import heappush, heappop, heapify

nums = [0, 1, 2, 3, 4, 5]

# 1. min heap
# 1) heapify
min_heap = [*nums]
heapify(min_heap)

# 2) heappush
heappush(min_heap, 6)

# 2) top and pop
while min_heap:
    print('top', min_heap[0], end=" ") # top 0 top 1 top 2 top 3 top 4 top 5 top 6
    heappop(min_heap)

print()

# 2. max heap
# 1) heapify
max_heap = [-num for num in nums]
heapify(max_heap)

# 2) heappush
heappush(max_heap, -6)

# 3) top and pop
while max_heap:
    print('top', -max_heap[0], end=" ") # top 6 top 5 top 4 top 3 top 2 top 1 top 0 
    heappop(max_heap)
```

### 2. Java
- min heap (default)
기본적으로 min heap이 제공됩니다. max heap이 필요한 경우 비교함수를 넣어줍니다.
```java
import java.util.Arrays;
import java.util.Comparator;
import java.util.PriorityQueue;

class Main {
    public static void main(String[] args) {
        Integer[] nums = {0, 1, 2, 3, 4, 5};

        // 1. min heap
        PriorityQueue<Integer> minHeap = new PriorityQueue<>();

        // 1) heapify
        minHeap.addAll(Arrays.asList(nums));

        // 2) add
        minHeap.add(6);

        // 3) top and pop
        while (!minHeap.isEmpty()) {
            System.out.print("top " + minHeap.peek() + " "); // top 0 top 1 top 2 top 3 top 4 top 5 top 6 
            minHeap.poll();
        }

        System.out.println();

        // 2. max heap
        PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Comparator.comparingInt(v -> -v));

        // 1) heapify
        maxHeap.addAll(Arrays.asList(nums));

        // 2) add
        maxHeap.add(6);

        // 3) top and pop
        while (!maxHeap.isEmpty()) {
            System.out.print("top " + maxHeap.peek() + " "); // top 6 top 5 top 4 top 3 top 2 top 1 top 0 
            maxHeap.poll();
        }
    }
}
```

### 3. JavaScript
시간 내에 할 수 있다면 정렬을 사용한다.

자바스크립트로 힙을 구현해서 사용할수도 있지만, 시간이 오래걸린다.

주관적인 의견으로 빌트인 자료구조를 사용하지 못하기 때문에 형평성 이슈가 있다.
```js
const q = [0, 1, 2, 3, 4, 5]

// 1. min heap
const a = []
q.forEach(x => a.push(x))
a.sort((a, b) => a-b)

// 2. max heap
const b = []
q.forEach(x => b.push(x))
a.sort((a, b) => b-a)
```

### 4. C++
- max heap(default)     
priority_queue는 기본적으로 max heap이기 때문에 minheap이 필요한 경우 cmp 오퍼레이터터를 오버라이딩 합니다. 또는 `greater<int>`를 사용합니다.

- 객체   
우선순위 큐에 객체가 들어가는 경우에도 cmp 오퍼레이터를 오버라이딩해서 사용합니다.
```c
#include <iostream>
#include <queue>

using namespace std;

struct minCmp {
    bool operator()(int& l, int& r) {
        return l > r;
    }
};

int nums[6] = {0, 1, 2, 3, 4, 5};

int main() {
    // 1. min heap
    // 1) heapify
    priority_queue<int, vector<int>, minCmp> minHeap(nums, nums + 6);

    // 2) heappush
    minHeap.push(6);

    // 3) top and pop
    while (!minHeap.empty()) {
        cout << "top " << minHeap.top() << " ";  // top 0 top 1 top 2 top 3 top 4 top 5 top 6
        minHeap.pop();
    }

    cout << endl;

    // 2. max heap
    priority_queue<int> maxHeap(nums, nums + 6);

    // 2) heappush
    maxHeap.push(6);

    // 3) top and pop
    while (!maxHeap.empty()) {
        cout << "top " << maxHeap.top() << " ";  // top 6 top 5 top 4 top 3 top 2 top 1 top 0
        maxHeap.pop();
    }
}
```