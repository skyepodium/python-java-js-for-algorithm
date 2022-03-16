[백준 11404 플로이드](https://www.acmicpc.net/problem/11404) - 플로이드

# 1. python
```python
import sys
input = sys.stdin.readline
print = sys.stdout.write


# 1. input
n = int(input())
m = int(input())
MAX_COST = 1e7 + 1
d = [[MAX_COST for _ in range(n+1)] for _ in range(n+1)]

# # 2. init
for i in range(0, n+1):
    d[i][i] = 0

# 3. graph
for _ in range(m):
    a, b, c = map(int, input().split())
    d[a][b] = min(d[a][b], c)

# 4. floyd
# 순서 꼭 지켜야 한다. k,i,j
for k in range(1, n+1):
    for i in range(1, n+1):
        for j in range(1, n+1):
            d[i][j] = min(d[i][j], d[i][k] + d[k][j])

for i in range(1, n+1):
    for j in range(1, n+1):
        if d[i][j] == MAX_COST: print("0 ")
        else: print("%d " % d[i][j])
    print("\n")
```

# 2. java
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

class Main {

    public static int n, m, a, b, c;
    public static int[][] d;
    public static final int MAX_COST = 10000001;
    public static void main(String[] args) throws IOException {
        // 1. setting
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st;

        // 2. input
        st = new StringTokenizer(br.readLine());
        n = Integer.parseInt(st.nextToken());
        st = new StringTokenizer(br.readLine());
        m = Integer.parseInt(st.nextToken());
        d = new int[n+1][n+1];

        for(int i=0; i<=n; i++) {
            for(int j=0; j<=n; j++){
                if(i != j) d[i][j] = MAX_COST;
            }
        }

        // 3. graph
        for(int i=0; i<m; i++) {
            st = new StringTokenizer(br.readLine());
            a = Integer.parseInt(st.nextToken());
            b = Integer.parseInt(st.nextToken());
            c = Integer.parseInt(st.nextToken());

            d[a][b] = Math.min(d[a][b], c);
        }

        // 4. floyd
        // 순서 꼭 지켜야 한다. k,i,j
        for(int k=1; k<=n; k++) {
            for(int i=1; i<=n; i++) {
                for(int j=1; j<=n; j++) {
                    d[i][j] = Math.min(d[i][j], d[i][k] + d[k][j]);
                }
            }
        }

        for(int i=1; i<=n; i++) {
            for(int j=1; j<=n; j++) {
                if(d[i][j] == MAX_COST) System.out.print("0 ");
                else System.out.print(d[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```