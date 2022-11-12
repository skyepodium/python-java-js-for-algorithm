# 1. 설명
- 1번 과목부터 N번 과목까지 차례대로 최소 몇 학기에 이수할 수 있는지를 한 줄에 공백으로 구분하여 출력


[문제 링크](https://www.acmicpc.net/problem/14567)


# 2. 코드
### 1) python
```python
import sys
input = sys.stdin.readline

from collections import deque

n, m = map(int, input().split())
v = [[] for _ in range(n+1)]
ind = [0] * (n + 1)
res = [0] * (n + 1)

for _ in range(m):
    s, e = map(int, input().split())
    ind[e] += 1
    v[s].append(e)

q = deque()
for i in range(1, n+1):
    if ind[i] == 0:
        res[i] = 1
        q.append(i)

while q:
    node = q.popleft()

    for n_node in v[node]:
        ind[n_node] -= 1
        res[n_node] = res[node] + 1

        if ind[n_node] == 0:
            q.append(n_node)

print(" ".join([str(i) for i in res[1:]]))
```

### 2) java
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

class Main {
    public static int MAX_N = 1001;
    public static int n, m, s, e, ind[], dist[];
    public static List<Integer>[] v;
    public static Queue<Integer> q = new LinkedList<>();
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());

        n = Integer.parseInt(st.nextToken());
        m = Integer.parseInt(st.nextToken());

        ind = new int[n+1];
        dist = new int[n+1];
        v = new ArrayList[n+1];

        for(int i=0; i<=n; i++) {
            v[i] = new ArrayList<>();
        }

        for(int i=0; i<m; i++) {
            st = new StringTokenizer(br.readLine());
            s = Integer.parseInt(st.nextToken());
            e = Integer.parseInt(st.nextToken());
            v[s].add(e);
            ind[e]++;
        }

        for(int i=1; i<=n; i++) {
            if(ind[i] == 0) {
                dist[i] = 1;
                q.add(i);
            }
        }

        while(!q.isEmpty()) {
            int node = q.poll();

            for(int nNode: v[node]) {
                ind[nNode]--;
                dist[nNode] = dist[node] + 1;
                if(ind[nNode] == 0) {
                    q.add(nNode);
                }
            }
        }

        for(int i=1; i<=n; i++) {
            System.out.print(dist[i] + " ");
        }
        System.out.println();
    }
}
```

### 3) C++
```cpp
#include <iostream>
#include <queue>
#include <vector>
#define MAX_INT 1001
using namespace std;

int n, m, s, e, ind[MAX_INT], res[MAX_INT];
vector<int> v[MAX_INT];
queue<int> q;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(0);
    cout.tie(0);

    cin >> n >> m;

    for (int i = 0; i < m; i++) {
        cin >> s >> e;
        v[s].push_back(e);
        ind[e]++;
    }

    for (int i = 1; i <= n; i++) {
        if (ind[i] == 0) {
            res[i] = 1;
            q.push(i);
        }
    }

    while (!q.empty()) {
        int node = q.front();
        q.pop();

        for (auto nNode : v[node]) {
            ind[nNode]--;
            res[nNode] = res[node] + 1;
            if (ind[nNode] == 0) {
                q.push(nNode);
            }
        }
    }

    for (int i = 1; i <= n; i++) {
        cout << res[i] << " ";
    }
    cout << endl;
}
```