[백준 2252 줄 세우기](https://www.acmicpc.net/problem/2252) - 위상정렬

# 1. 정리
### 1) DAG
위상정렬은 사이클이 없는 단방향 그래프 DAG(Directed Acyclic Graph) 에서만 사용가능하다.

### 2) 응용
순서를 계산하는 문제 및 줄세우는 비교 문제에 주로 사용된다.

# 1. python
```python
from collections import deque

# 1. input
n, m = map(int, input().split())
ind = [0] * (n+1)
v = [[] for _ in range(n+1)]

# 2. graph
for _ in range(m):
    a, b = map(int, input().split())
    # 단방향 그래프
    # 위상정렬은 사이클이 없는 단방향 그래프 DAG(Directed Acyclic Graph) 에서만 사용가능하다.
    v[a].append(b)
    ind[b] += 1

# 3. 위상정렬
def topological_sort():
    q = deque()
    for i in range(1, n+1):
        if ind[i] == 0: q.append(i)

    while q:
        node = q.popleft()
        print(node, end=" ")

        for n_node in v[node]:
            # 현재 노드 기준 인접 노드의 ind를 1 감소시킨다.
            ind[n_node] -= 1

            # ind가 0이되면 큐에 넣는다.
            if ind[n_node] == 0:
                q.append(n_node)
    print()

topological_sort()
```

# 2. java
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

class Main {
    public static int n, m, a, b;
    public static List<Integer>[] v;
    public static int[] ind;
    public static void main(String[] args) throws IOException {
        // 0. setting
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st;

        // 1. input
        st = new StringTokenizer(br.readLine());
        n = Integer.parseInt(st.nextToken());
        m = Integer.parseInt(st.nextToken());

        v = new ArrayList[n+1];
        ind = new int[n+1];
        for(int i=0; i<=n; i++) v[i] = new ArrayList<>();

        // 2. make graph
        for(int i=0; i<m; i++) {
            st = new StringTokenizer(br.readLine());
            a = Integer.parseInt(st.nextToken());
            b = Integer.parseInt(st.nextToken());

            // 단방향 그래프
            // 위상정렬은 사이클이 없는 단방향 그래프 DAG(Directed Acyclic Graph) 에서만 사용가능하다.
            v[a].add(b);
            ind[b]++;
        }

        // 3. 위상정렬
        topologicalSort();
    }

    public static void topologicalSort() {
        Queue<Integer> q = new LinkedList<>();
        for(int i=1; i<=n; i++) {
            if(ind[i] == 0) q.add(i);
        }

        while(!q.isEmpty()) {
            int node = q.poll();
            System.out.print(node + " ");

            for(int nNode: v[node]) {
                // 현재 노드 기준 인접 노드의 ind를 1 감소시킨다.
                ind[nNode]--;

                // ind가 0이되면 큐에 넣는다.
                if(ind[nNode] == 0) {
                    q.add(nNode);
                }
            }
        }

        System.out.println();
    }
}
```