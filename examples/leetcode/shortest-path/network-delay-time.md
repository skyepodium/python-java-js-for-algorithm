# 1. 설명
- 최단 경로를 구하세요.


[문제 링크](https://leetcode.com/problems/network-delay-time/)

# 2. 코드
### 1) python
```python
from heapq import heappush, heappop

class Solution:
    def networkDelayTime(self, times: List[List[int]], n: int, k: int) -> int:
        # 1. init
        max_val = 10001
        res = 0
        d = [max_val for _ in range(n+1)]
        v = [[] for _ in range(n+1)]
        
        # 2. make graph
        for s, e, c in times:
            v[s].append((c, e))
        
        # 3. dijkstra
        def dijkstra(start_node):
            pq = []
            d[start_node] = 0
            heappush(pq, (d[start_node], start_node))
            
            while pq:
                cost, node = heappop(pq)
                
                if d[node] < cost:
                    continue
                
                for n_cost, n_node in v[node]:
                    if d[n_node] > d[node] + n_cost:
                        d[n_node] = d[node] + n_cost
                        heappush(pq, (d[n_node], n_node))
        
        dijkstra(k)
        
        # 4. check
        for i in range(1, n+1):
            res = max(res, d[i])
            
        return -1 if res == max_val else res
        
```

### 2) java
```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.PriorityQueue;

class Solution {
    int max_val = 10001;
    int res = 0;
    int[] d;
    ArrayList<Node>[] v;
    public int networkDelayTime(int[][] times, int n, int k) {
        // 1. init
        v = new ArrayList[n+1];
        d = new int[n+1];
        for(int i=0; i<=n; i++) {
            v[i] = new ArrayList<>();
            d[i] = max_val;
        }

        // 2. make graph
        for(int[] time: times) {
            int s = time[0];
            int e = time[1];
            int c = time[2];
            v[s].add(new Node(e, c));
        }

        dijkstra(k);

        // 3. check loop
        for(int i=1; i<=n; i++) {
            res = Math.max(res, d[i]);
        }

        return res == max_val ? -1 : res;
    }

    public void dijkstra(int startNode) {
        d[startNode] = 0;
        PriorityQueue<Node> pq = new PriorityQueue<>(new Comparator<Node>() {
            @Override
            public int compare(Node o1, Node o2) {
                return o1.cost - o2.cost;
            }
        });
        pq.add(new Node(startNode, d[startNode]));

        while(!pq.isEmpty()) {
            Node cur = pq.poll();

            int node = cur.node;
            int cost = cur.cost;

            if(d[node] < cost) continue;

            for(Node next: v[node]) {
                int n_node = next.node;
                int n_cost = next.cost;

                if(d[n_node] > d[node] + n_cost) {
                    d[n_node] = d[node] + n_cost;
                    pq.add(new Node(n_node, d[n_node]));
                }
            }
        }
    }
}

class Node {
    int node, cost;

    public Node(int node, int cost) {
        this.node = node;
        this.cost = cost;
    }
}
```