# 순열

# 1. 내용
### 1) 시간복잡도
`O(n!)` 이고 `11!` 이 약 3천만 이기 때문에

순열은 대략 n이 10 이하인 경우에만 사용가능합니다.

### 2) built-in
- C++, Python - Built-in 사용
- Java, JavaScript - DFS 구현


# 2. 코드
### 1) Python
- itertools
```python
from itertools import permutations

n = 3

r = [x for x in permutations([_ for _ in range(n)])]

print('r', r)
# r [(0, 1, 2), (0, 2, 1), (1, 0, 2), (1, 2, 0), (2, 0, 1), (2, 1, 0)]
```

- DFS
```python
n = 3

permutations = []
check = [False for _ in range(n)]

def dfs(cnt, l):
    if cnt >= n:
        permutations.append(l[::])
        return

    for i in range(n):
        if not check[i]:
            check[i] = True
            l.append(i)
            dfs(cnt + 1, l)
            check[i] = False
            l.pop()

dfs(0, [])

print(permutations)
# [[0, 1, 2], [0, 2, 1], [1, 0, 2], [1, 2, 0], [2, 0, 1], [2, 1, 0]]
```

### 2) Java
```java
import java.util.ArrayList;
import java.util.List;
import java.util.Stack;

class Main {
    static int n = 3;
    static List<List<Integer>> permutation = new ArrayList<>();
    static boolean[] check = new boolean[n];
    public static void main(String[] args) {

        dfs(0, new Stack<>());

        for(List<Integer> p: permutation) {
            p.forEach(x -> System.out.print(x + " "));
            System.out.println();
        }
    }

    public static void dfs(int cnt, Stack<Integer> l) {
        if(cnt >= n) {
            permutation.add(new ArrayList<>(l));
            return;
        }

        for(int i=0; i<n; i++) {
            if(!check[i]) {
                check[i] = true;
                l.add(i);
                dfs(cnt + 1, l);
                check[i] = false;
                l.pop();
            }
        }
    }
}
```

### 3) JavaScipt
```js
const n = 3

const check = Array.from(Array(n).fill(false))
const permutation = []

// 2. dfs
const dfs = (cnt, l) => {
    if(cnt >= n) {
        permutation.push([...l])
        return
    }

    for(let i=0; i<n; i++) {
        if(!check[i]) {
            check[i] = true
            l.push(i)
            dfs(cnt + 1, l)
            check[i] = false
            l.pop()
        }
    }
}

dfs(0, [])

console.log(...permutation)
// [ 0, 1, 2 ] [ 0, 2, 1 ] [ 1, 0, 2 ] [ 1, 2, 0 ] [ 2, 0, 1 ] [ 2, 1, 0 ]
```
