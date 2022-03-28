# 배열에서 최소, 최대값 찾기

빌트인 함수로 최대한 편하게 찾는 경우

# 1. Python
min, max를 사용합니다.
```python
a = [1, 2, 3, 4]

print(min(a)) # 1

print(max(a)) # 4
```

# 2. Java
- 컬렉션 - Collections.min, stream - min
- primitive array - stream - min

```java
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

class Main {
    public static void main(String[] args) {
        // 1. 리스트
        List<Integer> a = Arrays.asList(1, 2, 3, 4);

        System.out.println(Collections.min(a)); // 1

        System.out.println(Collections.max(a)); // 4

        // 2. boxed 배열
        Integer[] b = {1, 2, 3, 4};

        System.out.println(Collections.min(Arrays.asList(b))); // 1

        System.out.println(Collections.max(Arrays.asList(b))); // 4

        // 3. primitive 배열
        int[] c = {1, 2, 3, 4};
        System.out.println(Arrays.stream(c).min().getAsInt()); // 1

        System.out.println(Arrays.stream(c).max().getAsInt()); // 4
    }
}
```

# 3. JavaScript
Math.min, max와 destructingd을 함께 사용합니다.
```js
const a = [1, 2, 3, 4]

console.log(Math.min(...a)) // 1

console.log(Math.max(...a)) // 4
```
