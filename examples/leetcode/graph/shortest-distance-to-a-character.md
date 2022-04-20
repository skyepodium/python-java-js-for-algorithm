# 1. 설명
- 주어진 문자와의 최소거리를 구하세요


[문제 링크](https://leetcode.com/problems/shortest-distance-to-a-character/)

# 2. 코드
### 1) Python
```python
class Solution:
    def shortestToChar(self, s: str, c: str) -> List[int]:
        # 1. init
        idx_list = [idx for idx, w in enumerate(s) if w == c]
        n = len(s)
        check = [-1 for _ in range(n)]

        # 2. bfs
        def bfs():
            q = deque(idx_list)
            for idx in idx_list:
                check[idx] = 0

            while q:
                node = q.popleft()

                n_node_list = [node - 1, node + 1]
                for n_node in n_node_list:
                    if n_node < 0 or n_node >= n: continue

                    if check[n_node] != -1: continue
                    check[n_node] = check[node] + 1
                    q.append(n_node)

        bfs()

        return check
```

### 2) Java
```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public int[] shortestToChar(String s, char c) {
        // 1. init
        int n = s.length();
        Queue<Integer> q = new LinkedList<>();
        int[] check = new int[n];
        for(int i=0; i<n; i++) {
            check[i] = -1;
            if(s.charAt(i) == c) {
                q.add(i);
                check[i] = 0;
            }
        }

        return bfs(n, q, check);
    }

    public int[] bfs(int n, Queue<Integer> q, int[] check) {
        while(!q.isEmpty()) {
            int node = q.poll();

            int[] nNodeList = {node - 1, node + 1};

            for(int nNode: nNodeList) {
                if(nNode < 0 || nNode >= n) continue;
                if(check[nNode] != -1) continue;

                check[nNode] = check[node] + 1;
                q.add(nNode);
            }
        }
        return check;
    }
}
```

### 3) JavaScript
```js
const shortestToChar = (s, c) => {
    // 1. init
    const n = s.length
    const q = s.split("")
                    .map((w, idx) => [w, idx])
                    .filter(([w, idx]) => w === c)
                    .map(([w, idx]) => idx)

    const check = Array.from(new Array(n)).fill(-1)
    q.forEach(x => check[x] = 0)

    // 2. bfs
    const bfs = () => {
        while(q.length > 0) {
            const node = q.shift()

            const nNodeList = [node - 1, node + 1]
            for(const nNode of nNodeList) {
                if(nNode < 0 || nNode >= n) continue
                if(check[nNode] !== -1) continue

                check[nNode] = check[node] + 1
                q.push(nNode)
            }
        }
    }

    bfs()

    return check
};
```