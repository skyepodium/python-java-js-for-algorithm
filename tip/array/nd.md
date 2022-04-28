# 다차원 배열 생성

### 1. Python
리스트 컴프리헨션을 반복해서 사용해줍니다.
```python
n, m = 1, 2
a = [[-1 for _ in range(m)] for _ in range(n)]
print('a', a)
# a [[-1, -1]]

n, m, k = 1, 2, 3
b = [[[-1 for _ in range(k)] for _ in range(m)] for _ in range(n)]
print('b', b)
# b [[[-1, -1, -1], [-1, -1, -1]]]
```

### 2. Java
자바는 크게 문제될 것은 없다.
```java
class Main {
    public static void main(String[] args) {
        int n = 1;
        int m = 2;
        int k = 3;

        int[][] a = new int[n][m];
        int[][][] b = new int[n][m][k];
    }
}
```

### 3. JavaScript
3차원 부터는 `Array.from`을 중첩해서 사용해줍니다.
```js
const n = 1
const m = 2
const k = 3

const a = Array.from(new Array(n), () => new Array(m).fill(-1))

console.log('a', a)
// a [ [ -1, -1 ] ]

const b = Array.from(new Array(n),
    () => Array.from(new Array(m),
        () => new Array(k)
            .fill(-1)))

console.log('b', b)
// b [ [ [ -1, -1, -1 ], [ -1, -1, -1 ] ] ]
```