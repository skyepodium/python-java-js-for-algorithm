[백준 1929 소수 구하기](https://www.acmicpc.net/problem/1929) - 에라토스테네스의 체

# 1. 참고
약수의 범위는 2 ~ sqrt(n) + 1 `제곱수` 까지만 진행한다.

제곱수보다 큰 소수가 아닌 수는 이미 지워졌기 때문에 반복할 필요가 없다.

제곱수까지 반복
### 1) python
```python
for i in range(2, n ** 0.5 + 1)
```
### 2) java
```java
for(int i=2; i*i<=n; i++)
```

# 1. python
```python
# 1. input
m, n = map(int, input().split())
check = [False] * (n+1)

# 2. eratos
def eratos():
    # exception
    check[1] = True

    for i in range(2, int(n ** 0.5 + 1)):
        for j in range(i*2, n+1, i):
            if not check[j]:
                check[j] = True

eratos()

for i in range(m, n+1):
    if not check[i]: print(i)
```

# 2. java
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

class Main {
    public static int n, m;
    public static boolean[] check;
    public static void main(String[] args) throws IOException {
        // 1. setting
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());

        // 2. input
        m = Integer.parseInt(st.nextToken());
        n = Integer.parseInt(st.nextToken());
        check = new boolean[n + 1];

        eratos();

        for(int i=m; i<=n; i++) {
            if(!check[i]) System.out.println(i);
        }
    }

    public static void eratos() {
        // exception
        check[1] = true;

        for(int i=2; i*i<=n; i++) {
            for(int j=i*2; j<=n; j+=i) {
                if(!check[j]) check[j] = true;
            }
        }
    }
}
```