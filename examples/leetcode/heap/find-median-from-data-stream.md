# 1. 설명
- 중앙값을 구하세요.
- max heap, min heap을 사용해서 중앙값을 계산합니다.


[문제 링크](https://leetcode.com/problems/find-median-from-data-stream/)

# 2. 코드
### 1) Python
```python
from heapq import heappush, heappop

class MedianFinder:

    def __init__(self):
        self.min_heap = []
        self.max_heap = []

    def addNum(self, num: int) -> None:
        if len(self.max_heap) < 1:
            heappush(self.max_heap, -num)
            return

        if num < -self.max_heap[0]:
            heappush(self.max_heap, -num)
        else:
            heappush(self.min_heap, num)

        if len(self.max_heap) >= len(self.min_heap) + 2:
            heappush(self.min_heap, -heappop(self.max_heap))
        elif len(self.max_heap) < len(self.min_heap):
            heappush(self.max_heap, -heappop(self.min_heap))

        return

    def findMedian(self) -> float:
        if len(self.max_heap) == len(self.min_heap):
            return (-self.max_heap[0] + self.min_heap[0]) / 2.0

        return -float(self.max_heap[0])

```

### 2) Java
```java
class MedianFinder {
    PriorityQueue<Double> minHeap;
    PriorityQueue<Double> maxHeap;

    public MedianFinder() {
        this.minHeap = new PriorityQueue<>(Comparator.comparingDouble(v -> v));
        this.maxHeap = new PriorityQueue<>(Comparator.comparingDouble(v -> -v));
    }

    public void addNum(int num) {
        if(this.maxHeap.isEmpty()) {
            maxHeap.add((double) num);
            return;
        }

        if(num <= maxHeap.peek()) {
            maxHeap.add((double) num);
        } else {
            minHeap.add((double) num);
        }

        if(this.maxHeap.size() >= this.minHeap.size() + 2) {
            this.minHeap.add(this.maxHeap.poll());
        } else if(this.maxHeap.size() <this.minHeap.size()) {
            this.maxHeap.add(this.minHeap.poll());
        }
    }

    public double findMedian() {
        if(this.maxHeap.size() == this.minHeap.size()) {
            return (this.maxHeap.peek() + this.minHeap.peek()) / 2;
        }

        return this.maxHeap.peek();
    }
}
```

### 3) C++
```cpp
#include <queue>

using namespace std;
class MedianFinder {
    struct cmp {
        bool operator()(double a, double b) {
            return a > b;
        }
    };

   private:
    priority_queue<double> maxHeap;
    priority_queue<double, vector<double>, cmp> minHeap;

   public:
    MedianFinder() {
        maxHeap = priority_queue<double>();
        minHeap = priority_queue<double, vector<double>, cmp>();
    }

    void addNum(int num) {
        if (maxHeap.empty()) {
            maxHeap.push(num);
            return;
        }

        if (num <= maxHeap.top()) {
            maxHeap.push(num);
        } else {
            minHeap.push(num);
        }

        if (maxHeap.size() >= minHeap.size() + 2) {
            minHeap.push(maxHeap.top());
            maxHeap.pop();
        } else if (maxHeap.size() < minHeap.size()) {
            maxHeap.push(minHeap.top());
            minHeap.pop();
        }
    }

    double findMedian() {
        if (maxHeap.size() == minHeap.size()) {
            return (maxHeap.top() + minHeap.top()) / 2.0;
        }

        return maxHeap.top();
    }
};
```

