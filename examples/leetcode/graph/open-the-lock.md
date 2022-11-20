# 1. 설명
- BFS로 최단거리를 구하는 문제입니다.
- 다만 이 문제의 경우 시작, 끝 좌표가 주어졌기 때문에 양방향 BFS를 사용할 수 있습니다.

[문제 링크](https://leetcode.com/problems/open-the-lock/)

# 2. 코드
### 1) python
```python
from typing import List

class Solution:
    def openLock(self, deadends: List[str], target: str) -> int:
        # 1. init
        visited = set(deadends)
        check = set()

        # 2. move_bit
        def move_bit(node, idx, direction):
            if direction == 1:
                next_bit = (int(node[idx]) + 1) % 10
            else:
                next_bit = (int(node[idx]) - 1) % 10
            if next_bit >= 10:
                next_bit = 0
            elif next_bit < 0:
                next_bit = 9
            return node[:idx] + str(next_bit) + node[idx+1:]


        # 3. bfs
        def bfs(start_node, target_node):
            q1 = set([start_node])
            q2 = set([target_node])
            step = 0

            while q1 and q2:
                if len(q1) > len(q2):
                    q1, q2 = q2, q1
                    
                temp = set()

                for node in q1:
                    if node in deadends:
                        continue

                    if node in q2:
                        return step

                    visited.add(node)

                    for i in range(4):
                        for j in [-1, 1]:
                            next_node = move_bit(node, i, j)
                            if next_node in visited:
                                continue
                            temp.add(next_node)

                q1 = q2
                q2 = temp
                step += 1

            return -1

        return bfs("0000", target)
```

### 2) java
```java
import java.util.Arrays;
import java.util.HashSet;

class Solution {
    public int openLock(String[] deadends, String target) {

        return bfs("0000", target, deadends);
    }

    public String getNextNode(String node, int index, int direction) {
        StringBuilder sb = new StringBuilder(node);

        // up
        int nextBit = 0;
        if(direction == 0) {
            nextBit = (node.charAt(index) - '0' + 1) % 10;
        }

        // down
        if(direction == 1) {
            nextBit = (node.charAt(index) - '0' - 1 + 10) % 10;
        }

        return sb.replace(index, index + 1, String.valueOf(nextBit)).toString();
    }

    public int bfs(String startNode, String endNode, String[] deadends) {
        HashSet<String> q1 = new HashSet<>();
        HashSet<String> q2 = new HashSet<>();
        q1.add(startNode);
        q2.add(endNode);

        HashSet<String> visited = new HashSet<>(Arrays.asList(deadends));
        int step = 0;

        while(!q1.isEmpty() && !q2.isEmpty()) {
            if (q1.size() > q2.size()) {
                HashSet<String> tmp = q1;
                q1 = q2;
                q2 = tmp;
            }

            HashSet<String> temp = new HashSet<>();

            for(String node: q1) {
                if(visited.contains(node)) continue;
                if(q2.contains(node)) return step;
                visited.add(node);

                for(int i=0; i<4; i++) {
                    for(int j=0; j<2; j++) {
                        String nextNode = getNextNode(node, i, j);
                        if(visited.contains(nextNode)) continue;
                        temp.add(nextNode);
                    }
                }
            }
            q1 = q2;
            q2 = temp;
            step++;
        }
        return -1;
    }
}

class Main {
    public static void main(String[] args) {
        String[] deadends = {"0201","0101","0102","1212","2002"};
        String target = "0202";

        Solution sl = new Solution();
        System.out.println(sl.openLock(deadends, target));
    }
}
```

### 3) JavaScript
```js
const openLock = (deadends, target) => {
    // 1. getNextNode
    const getNextNode = (node, index, direction) => {
        let nextBit = 0
        // up
        if(direction === 0) {
            nextBit = (Number(node[index]) + 1) % 10
        }
        // down
        if(direction === 1) {
            nextBit = (Number(node[index]) - 1 + 10) % 10
        }

        return node.slice(0, index) + nextBit + node.slice(index + 1)
    }

    // 2. BFS
    const bfs = (startNode, endNode, deadends) => {
        // 1) init
        let q1 = new Set()
        let q2 = new Set()
        const visited = new Set()
        q1.add(startNode)
        q2.add(endNode)
        deadends.forEach(deadend => visited.add(deadend))

        // 2) loop
        let step = 0
        while (q1.size > 0 && q2.size > 0) {
            if(q1.size > q2.size) {
                [q1, q2] = [q2, q1]
            }
            const temp = new Set()

            for(const node of q1) {
                if(visited.has(node)) continue
                if(q2.has(node)) return step
                visited.add(node)

                for(let i=0; i<4; i++){
                    for(let j=0; j<2; j++) {
                        const nextNode = getNextNode(node, i, j)
                        if(visited.has(nextNode)) continue
                        temp.add(nextNode)
                    }
                }
            }
            q1 = q2
            q2 = temp
            step++
        }
        return -1
    }

    return bfs('0000', target, deadends)
};
```

### 4) C++
```c
class Solution {
   public:
    int openLock(vector<string>& deadends, string target) {
        return bfs("0000", target, deadends);
    }

    string getNextNode(string node, int index, int direction) {
        if (direction == 0) {
            node[index] = node[index] == '9' ? '0' : node[index] + 1;
        } else {
            node[index] = node[index] == '0' ? '9' : node[index] - 1;
        }
        return node;
    }

    int bfs(string startNode, string endNode, vector<string>& deadends) {
        set<string> visited;
        set<string> q1, q2;
        int step = 0;
        for (auto deadend : deadends) {
            visited.insert(deadend);
        }
        q1.insert(startNode);
        q2.insert(endNode);

        while (!q1.empty() && !q2.empty()) {
            if (q1.size() > q2.size()) {
                swap(q1, q2);
            }
            set<string> temp = {};
            for (auto node : q1) {
                if (visited.find(node) != visited.end()) continue;
                if (q2.find(node) != q2.end()) return step;
                visited.insert(node);

                for (int i = 0; i < 4; i++) {
                    for (int j = 0; j < 2; j++) {
                        string nextNode = getNextNode(node, i, j);
                        if (visited.find(nextNode) != visited.end()) continue;
                        temp.insert(nextNode);
                    }
                }
            }
            q1 = q2;
            q2 = temp;
            step++;
        }
        return -1;
    };
};
```