# 우선순위 큐

# 요약
- python - heapq
- java - PriorityQueue
- JavaScript- 빌트인 자료구조가 없다. 시간복잡도 이내면 정렬을 사용하고, 없으면 직접구현

### 1) 일반
코딩테스트에서 3가지 언어 모두 사용 가능한데 자바스크립트 힙이 필요하면 조금 의심해봐야한다.

### 2) 다익스트라
다익스트라 알고리즘의 경우 다음 문체처럼 우선순위큐 대신 일반 큐를 사용해도 시간안에 들어오도록 설계된다.
[프로그래머스 - 경주로 건설
](https://programmers.co.kr/learn/courses/30/lessons/67259)
### 1. python
```python
from heapq import heappop, heappush, heapify

q = [0, 1, 2, 3, 4, 5]

# 1. min heap
a = []
for v in q:
   heappush(a, v)

# 2. map heap
b = []
for v in q:
    heappush(b, -v)
```

### 2. Java
```java
import java.util.Comparator;
import java.util.PriorityQueue;

class Main {
    public static void main(String[] args) {
        int[] q = {0, 1, 2, 3, 4, 5};

        // 1. min heap
        PriorityQueue<Integer> a = new PriorityQueue<>(Comparator.comparingInt(v -> v));
        for(int num: q) a.add(num);

        // 2. max heap
        PriorityQueue<Integer> b = new PriorityQueue<>((x, y) -> y-x);
        for(int num: q) b.add(num);
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