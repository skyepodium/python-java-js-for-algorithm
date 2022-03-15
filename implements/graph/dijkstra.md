# 1. python
```python
from heapq import heappush, heappop

# 입출력 빠르게 설정
import sys
input = sys.stdin.readline
print = sys.stdout.write

# 1. init
n, m = map(int, input().split())
start_node = int(input())
v = [[] for _ in range(n+1)]
MAX_COST = 2e6 # 2 * 10^6 의미
d = [MAX_COST] * (n + 1)


# 2. make graph
for _ in range(m):
    a, b, c = map(int, input().split())
    v[a].append((c, b))


# 3. dijkstra
def dijkstra(node):
    # 1) pq
    pq = []
    d[node] = 0
    heappush(pq, (d[node], node))

    # 2) loop
    while pq:
        c_cost, c_node = heappop(pq)

        # 3) exception
        '''
        바로 이전 노드에서 현재 노드까지 오는 비용 c_cost 가
        현재 노드의 최소도착 비용 d[c_node] 보다 큰 상황은
        이미 다른 탐색에서 최소 경로를 찾았고, 지금 경로는 필요없는 결로라는 의미
        이미 pq에 들어있을 때 비용이 변경되어 최신화 안된 경우로 
        set(Red Black Tree)를 사용하면 해결가능하다.
        '''
        if c_cost > d[c_node]: continue

        for n_cost, n_node in v[c_node]:
            if d[n_node] > d[c_node] + n_cost:
                d[n_node] = d[c_node] + n_cost
                heappush(pq, (d[n_node], n_node))


dijkstra(start_node)

for node in range(1, n+1):
    if d[node] == MAX_COST: print("INF\n")
    else: print("%d\n" % d[node])
```

# 2. java
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

class Main {

    public static int n, m, startNode, a, b, c;
    public static int MAX_VALUE = Integer.MAX_VALUE;
    public static List<Node>[] v; // ArrayList를 n+1 배열로 만들어서 인접리스트를 만든다.
    public static int[] d;

    public static void main(String[] args) throws IOException {
        // 0. setting
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st;

        // 1. input
        st = new StringTokenizer(br.readLine());
        n = Integer.parseInt(st.nextToken());
        m = Integer.parseInt(st.nextToken());

        st = new StringTokenizer(br.readLine());
        startNode = Integer.parseInt(st.nextToken());

        v = new ArrayList[n+1];
        d = new int[n+1];

        // 2. make graph
        for(int i=0; i<=n; i++) {
            d[i] = MAX_VALUE;
            v[i] = new ArrayList<>();
        }

        for(int i=0; i<m; i++) {
            st = new StringTokenizer(br.readLine());
            a = Integer.parseInt(st.nextToken());
            b = Integer.parseInt(st.nextToken());
            c = Integer.parseInt(st.nextToken());

            v[a].add(new Node(b, c));
        }

        // 3. dijkstra
        dijkstra(startNode);

        for(int i=1; i<=n; i++) {
            if(d[i] == MAX_VALUE) System.out.println("INF");
            else System.out.println(d[i]);
        }
    }

    public static void dijkstra(int startNode) {
        d[startNode] = 0;
        // 객체 비교 우선순위 큐
        PriorityQueue<Node> pq = new PriorityQueue<>((o1, o2) -> o1.cost - o2.cost);
        // 비교식을 더 단축할 수 있다.
        // PriorityQueue<Node> pq = new PriorityQueue<>(Comparator.comparingInt(o -> o.cost));

        pq.add(new Node(startNode, d[startNode]));

        while(!pq.isEmpty()) {
            Node node = pq.poll();
            int c_node = node.node;
            int c_cost = node.cost;

            /*
                바로 이전 노드에서 현재 노드까지 오는 비용 c_cost 가
                현재 노드의 최소도착 비용 d[c_node] 보다 큰 상황은
                이미 다른 탐색에서 최소 경로를 찾았고, 지금 경로는 필요없는 결로라는 의미
                이미 pq에 들어있을 때 비용이 변경되어 최신화 안된 경우로
                set(Red Black Tree)를 사용하면 해결가능하다.
             */
            if(d[c_node] < c_cost) continue;

            for(Node next: v[c_node]) {
                int n_node = next.node;
                int n_cost = next.cost;

                if(d[n_node] > d[c_node] + n_cost) {
                    d[n_node] = d[c_node] + n_cost;
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