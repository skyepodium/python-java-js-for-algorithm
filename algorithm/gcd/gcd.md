[백준 2609 최대공약수와 최소공배수](https://www.acmicpc.net/problem/2609) - gcd

# 1. 계산법
최대공약수 - 유클리드 호제법을 사용해서 계산한다.
최소공배수 - a * b / 최대 공악수

# 2. 참고
gcd 함수에 a, b를 넣는데 항상 a가 b 보다 크게 호출할 필요없다.
`gcd(b, a%b)` 에 의해 a가 b보다 크도록 바뀐다.

# 1. python
```python
a, b = map(int, input().split())

def gcd(a, b):
    return a if b == 0 else gcd(b, a%b)

print(gcd(a, b))
print(a * b // gcd(a, b))
```

# 2. java
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());

        int a = Integer.parseInt(st.nextToken());
        int b = Integer.parseInt(st.nextToken());

        System.out.println(gcd(a, b));
        System.out.println(a * b / gcd(a, b));
    }

    public static int gcd(int a, int b) {
        return b == 0 ? a : gcd(b, a%b);
    }
}
```