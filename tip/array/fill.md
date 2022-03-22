# 배열 0 ~ n-1 까지 초기화하기

# 1. Python
```python
n = 10
# 리스트 컴프리헨션으로 초기화
a = [x for x in range(n)]

print(*a) # 0 1 2 3 4 5 6 7 8 9
```

# 2. Java
```java
import java.util.Arrays;
import java.util.stream.IntStream;

class Main {
    public static void main(String[] args) {
        int n = 10;
        int[] a = IntStream.range(0, n).toArray();

        Arrays.stream(a).forEach(x -> System.out.print(x + " "));
        // 0 1 2 3 4 5 6 7 8 9
    }
}
```

# 3. JavaScript
```js
const n = 10

const a = Array.from(Array(n).keys())

console.log(...a) // 0 1 2 3 4 5 6 7 8 9
```