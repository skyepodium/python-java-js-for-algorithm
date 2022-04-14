# 배열 -> 리스트, 리스트 -> 배열 - 변환하기

크게 2가지로 나눠집니다.
1. 같은 자료형을 사용하는 경우

2. boxing, unboxing이 필요한 경우 - (int, double, float)

### 1. 같은 자료형을 사용하는 경우

- 리스트 -> 배열 - toArray를 사용합니다. 
- 배열 -> 리스트 - stream, collect를 사용합니다.

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

class Main {
    public static void main(String[] args) {

        List<String> a = new ArrayList<>();
        a.add("a");
        a.add("b");

        String[] b = a.toArray(new String[0]);
        Arrays.stream(b).forEach(System.out::println); // a, b

        a = Arrays.stream(b).collect(Collectors.toList());

        a.forEach(System.out::println); // a, b
    }
}
```

### 2) boxing, unboxing이 필요한 경우

기본적으로 toArray, stream-collect를 사용하는건 동일하지만, boxing, unboxing이 필요합니다.

- 리스트 - 참조
- 배열 - 원시

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

class Main {
    public static void main(String[] args) {

        List<Integer> a = new ArrayList<>();
        a.add(0);
        a.add(1);

        int[] b = a.stream().mapToInt(x -> x).toArray();
        Arrays.stream(b).forEach(System.out::println); // 0, 1

        a = Arrays.stream(b).boxed().collect(Collectors.toList());
        a.forEach(System.out::println); // 0, 1
    }
}
```