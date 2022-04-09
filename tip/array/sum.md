# 배열의 합 구하기

반복문 사용할 수 있지만, 더 편하게 하고 싶을 때

### 1. Python
builtin sum을 사용합니다.
```python
a = [1, 2, 3, 4, 5]

res = sum(a)

print(res) # 15
```

### 2. Java
stream을 사용합니다.
```java
import java.util.Arrays;

class Main {
    public static void main(String[] args) {
        int[] a = {1, 2, 3, 4, 5};

        int res = Arrays.stream(a).sum();

        System.out.println(res); // 15
    }
}
```

### 3. JavaScript
reduce를 사용합니다.
```js
const a = [1, 2, 3, 4, 5]

const res = a.reduce((prev, cur) => prev + cur)

console.log('res', res) // 15
```