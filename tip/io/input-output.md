# 입출력

# 1. python
### 1) 일반적인 입출력
```python
a = int(input())
print('a', a) # a 1

b, c = map(int, input().split())
print('b', b, 'c', c) # b 2 c 3

arr = list(map(int, input().split()))
print('arr', *arr) # arr 1 2 3 4
```

### 2) 빠른 입출력
```python
import sys
input = sys.stdin.readline
print = sys.stdout.write

a = int(input())
print(f"a {a}\n") # a 1

b, c = map(int, input().split())
print(f"b {b} c {c}\n") # b 2 c 3

arr = list(map(int, input().split()))
print(f"arr {' '.join(map(str, arr))}\n") # arr 1 2 3 4
```

# 2. Java
입력 속도 향상을 위해 반드시 BufferedReader를 사용합니다.

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st;

        st = new StringTokenizer(br.readLine());
        int a = Integer.parseInt(st.nextToken());
        System.out.println("a " + a); // a 1

        st = new StringTokenizer(br.readLine());
        int b = Integer.parseInt(st.nextToken());
        int c = Integer.parseInt(st.nextToken());
        System.out.println("b " + b + " c " + c); // b 2 c 3

        st = new StringTokenizer(br.readLine());
        int[] arr = new int[4];
        for(int i=0; i<4; i++) {
            arr[i] = Integer.parseInt(st.nextToken());
        }
        System.out.print("arr ");
        Arrays.stream(arr).forEach(x -> System.out.print(x + " "));
        // arr 1 2 3 4
    }
}
```

# 3. C++
### cin, cout
cin, cout을 그대로 사용하면 scanf, printf 보다 입출력 속도가 느리기 때문에 아래 설정을 추가합니다.

scanf, printf 만큼 속도가 빨라지고, 더 편하다는 장점이 있습니다.

하지만, 저 설정을 쓰면 printf, scanf로 입출력을 받으면 싱크가 안맞게 printf, scanf은 cin,cout과 함께 되어 사용할 수 없습니다.
```cpp
#include <iostream>

using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(0);
    cout.tie(0);
}
```