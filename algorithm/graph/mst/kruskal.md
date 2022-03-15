[최소 스패닝 트리](https://www.acmicpc.net/problem/1197) - 크루스칼

# 1. python
```python
# 1. init
n, m = map(int, input().split())
# 부모가 자기 자신이 되도록 초기화
d = [i for i in range(n+1)]
v = []
res = 0

# 2. input
for _ in range(m):
    start, end, cost = map(int, input().split())
    v.append((start, end, cost))

# 3. sort
# 가중치 오름 차순 그래프 정렬
v.sort(key=lambda x: x[2])


# 4. find
def find(node):
    if node == d[node]:
        return node
    else:
        # 최상위 부모 검색
        d[node] = find(d[node])
        return d[node]


for s, e, c in v:
    s, e = find(s), find(e)

    # union
    # 부모가 다르면 이어주고, 값을 더해준다.
    if s != e:
        d[s] = e
        res += c

print("%d" % res)
```

# 2. java
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.List;
import java.util.StringTokenizer;

class Main {

    public static int n, m, d[], start, end, cost, s, e, c, res;
    public static List<Graph> v = new ArrayList<>();
    public static void main(String[] args) throws IOException {
        // 0. setting
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st;

        // 1. init
        st = new StringTokenizer(br.readLine());
        n = Integer.parseInt(st.nextToken());
        m = Integer.parseInt(st.nextToken());

        d = new int[n+1];
        // 부모가 자기 자신이 되도록 초기화
        for(int i=0; i<=n; i++) d[i] = i;

        // 2. input
        for(int i=0; i<m; i++) {
            st = new StringTokenizer(br.readLine());
            start = Integer.parseInt(st.nextToken());
            end = Integer.parseInt(st.nextToken());
            cost = Integer.parseInt(st.nextToken());

            v.add(new Graph(start, end, cost));
        }

        v.sort((o1, o2) -> o1.cost - o2.cost);
        // 단축가능
        // v.sort(Comparator.comparingInt(o -> o.cost));

        for(Graph g: v) {
            s = find(g.start);
            e = find(g.end);
            c = g.cost;

            // union
            // 부모가 다르면 이어주고, 값을 더해준다.
            if(s != e) {
                d[s] = e;
                res += c;
            }
        }

        System.out.println(res);
    }

    public static int find(int node) {
        // 최상위 부모 검색
        if(node == d[node]) return node;
        else return d[node] = find(d[node]);
    }
}

class Graph {
    int start;
    int end;
    int cost;

    public Graph(int start, int end, int cost) {
        this.start = start;
        this.end = end;
        this.cost = cost;
    }
}
```