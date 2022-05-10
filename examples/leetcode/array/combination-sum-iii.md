# 1. 설명
- k개를 더해서 n이되는 조합을 구하세요

[문제 링크](https://leetcode.com/problems/combination-sum-iii/)

# 2. 코드
### 1) Python
```python
from typing import List


class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        # 1. init
        max_int = 10
        check = [False for _ in range(max_int)]
        res = []

        # 2. recursive
        def go(cnt, l, sum_val):
            if sum_val > n:
                return

            if cnt >= k:
                if sum_val == n:
                    res.append(l[::])
                return

            for i in range(1, max_int):
                if not check[i]:
                    if l and l[-1] > i: continue

                    check[i] = True
                    l.append(i)
                    go(cnt + 1, l, sum_val + i)
                    check[i] = False
                    l.pop()

        go(0, [], 0)

        return res
```

### 2) Java
```java
import java.util.ArrayList;
import java.util.List;
import java.util.Stack;

class Solution {
    List<List<Integer>> res = new ArrayList<>();
    boolean[] check = new boolean[10];
    public List<List<Integer>> combinationSum3(int k, int n) {

        go(0, new Stack<>(), 0, n, k);

        return res;
    }

    public void go(int cnt, Stack<Integer> s, int sumVal, int n, int k) {
        if(sumVal > n) return;

        if(cnt >= k) {
            if(sumVal == n)
                res.add(new ArrayList<>(s));
            return;
        }

        for(int i=1; i<10; i++) {
            if(!check[i]) {
                if(!s.isEmpty() && s.peek() > i) continue;

                check[i] = true;
                s.add(i);
                go(cnt + 1, s, sumVal + i, n, k);
                check[i] = false;
                s.pop();
            }
        }
    }
}
```

### 3) JavaScript
```js
const combinationSum3 = (k, n) => {
    // 1. init
    const res = []
    const check = Array.from(new Array(10).fill(false))

    // 2. recursive
    const go = (cnt, l, sumVal) => {
        if(sumVal > n) return

        if(cnt >= k) {
            if(sumVal === n) {
                res.push([...l])
            }
            return
        }

        for(let i=1; i<10; i++) {
            if(!check[i]) {
                if(l.length > 0 && l[l.length - 1] > i) continue

                check[i] = true
                l.push(i)
                go(cnt + 1, l, sumVal + i)
                check[i] = false
                l.pop()
            }
        }
    }

    go(0, [], 0)

    return res
};
```

### 4) TypeScript
```ts
const combinationSum3 = (k: number, n: number): number[][] => {
    // 1. init
    const res:number[][] = []
    const check:boolean[] = Array.from(new Array(10).fill(false))

    // 2. recursive
    const go = (cnt:number, l:number[], sumVal:number): void => {
        if(sumVal > n) return

        if(cnt >= k) {
            if(sumVal === n) {
                res.push([...l])
            }
            return
        }

        for(let i=1; i<10; i++) {
            if(!check[i]) {
                if(l.length > 0 && l[l.length - 1] > i) continue

                check[i] = true
                l.push(i)
                go(cnt + 1, l, sumVal + i)
                check[i] = false
                l.pop()
            }
        }
    }

    go(0, [], 0)

    return res
};
```