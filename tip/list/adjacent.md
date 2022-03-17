# 인접 리스트 생성

### 1. python
```python
n = 3

v = [] for _ in range(n)]
```

### 2. java
자바 조금 다르니 숙지 필요
```java
import java.util.ArrayList;
import java.util.List;

class Main {
    public static void main(String[] args) {
        int n = 3;

        List<Integer>[] v = new ArrayList[n+1];
        for(int i=0; i<=n; i++) {
            v[i] = new ArrayList<>();
        }
    }
}
```

### 3. JavaScript
```js
const n = 3

// 배열을 생성하고, map을 통해 각 배열 하나의 원소에 새로운 배열을 생성한다.
const v = Array.from(Array(n), () => [])
```