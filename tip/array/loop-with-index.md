# forEach 인덱스 함께 사용하기

python, js는 builtin으로 편하게 사용할 수 있지만, java는 조금 다릅니다.

- python - enumerate
- java - 1) 인덱스 스트림, 2. atomic
- JavaScript - builtin 지원 사용

# 1. Python
`enumerate` 를 사용합니다.
```python
a = [0, 1, 2, 3, 4, 5]

for idx, val in enumerate(a):
    print(idx, val)
```

# 2. Java
### 1) 인덱스 스트림
```java
import java.util.stream.IntStream;

class Main {
    public static void main(String[] args) {

        int[] a = {0, 1, 2, 3, 4, 5};

        IntStream.range(0, a.length)
                .forEach(idx -> System.out.println(a[idx] + " " + idx));
    }
}
```

### 2) atomic integer
스트림, 람다는 병렬처리로 외부 변수를 참조하는 경우 동시성이 보장되지 않습니다.

이를 위해서는 atomic 자료형을 사용하고, 이를 인덱스로 사용합니다.
```java
import java.util.Arrays;
import java.util.concurrent.atomic.AtomicInteger;

class Main {
    public static void main(String[] args) {

        int[] a = {0, 1, 2, 3, 4, 5};
        AtomicInteger idx = new AtomicInteger();
        Arrays.stream(a)
                .forEach(x -> System.out.println(a[idx.get()] + " " + idx.getAndIncrement()));
    }
}
```

### 2) 

# 3. JavaScript
builtin 함수에서 index는 두번째 인자로 사용가능합니다.
```js
const a = [0, 1, 2, 3, 4, 5]

a.forEach((val, idx) => console.log(val, idx))
```
