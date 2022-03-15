[백준 1260 DFS와 BFS](https://www.acmicpc.net/problem/1260) - DFS, BFS

# 1. python
```python
from collections import deque

# 1. init
n, m, start_node = map(int, input().split())
v = [[] for _ in range(n+1)]
check = []

# 2. make graph
for _ in range(m):
    a, b = map(int, input().split())
    v[a].append(b)
    v[b].append(a)

# 3. sort
for i in range(1, n+1):
    v[i].sort()


# 4. dfs
def dfs(node):
    check[node] = True
    print(node, end=" ")
    for n_node in v[node]:
        if check[n_node]: continue
        dfs(n_node)


# 5. bfs
def bfs(start):
    q = deque()
    q.append(start)
    check[start] = True

    while q:
        node = q.popleft()
        print(node, end=" ")

        for n_node in v[node]:
            if check[n_node]: continue
            check[n_node] = True
            q.append(n_node)


check = [False] * (n+1)
dfs(start_node)

print()

check = [False] * (n+1)
bfs(start_node)
```

# 2. java
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

class Main {
    public static int n, m, startNode, a, b;
    public static List<Integer>[] v;
    public static boolean[] check;

    public static void main(String[] args) throws IOException {
        // 1. input
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st;

        st = new StringTokenizer(br.readLine());
        n = Integer.parseInt(st.nextToken());
        m = Integer.parseInt(st.nextToken());
        startNode = Integer.parseInt(st.nextToken());

        // 2. make graph
        v = new ArrayList[n+1];
        for(int i=0; i<=n; i++) v[i] = new ArrayList<>();

        for(int i=0; i<m; i++) {
            st = new StringTokenizer(br.readLine());
            a = Integer.parseInt(st.nextToken());
            b = Integer.parseInt(st.nextToken());
            v[a].add(b);
            v[b].add(a);
        }

        // 3. 정렬
        for(int i=1; i<=n; i++) {
            v[i].sort((o1, o2) -> o1 - o2);
            // 단축 가능
            // v[i].sort(Comparator.comparingInt(o -> o));
        }

        check = new boolean[n+1];
        dfs(startNode);

        System.out.println();

        check = new boolean[n+1];
        bfs(startNode);
    }

    public static void dfs(int node) {
        check[node] = true;
        System.out.print(node + " ");

        for(int nNode: v[node]) {
            if(check[nNode]) continue;
            dfs(nNode);
        }
    }

    public static void bfs(int start) {
        Queue<Integer> q = new LinkedList<>();
        q.add(start);
        check[start] = true;

        while(!q.isEmpty()) {
            int node = q.poll();
            System.out.print(node + " ");

            for(int nNode: v[node]) {
                if(check[nNode]) continue;

                check[nNode] = true;
                q.add(nNode);
            }
        }
    }
}
```