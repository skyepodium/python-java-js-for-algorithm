# 1. 설명
- 순열을 구하세요


[문제 링크](https://leetcode.com/problems/permutations-ii/)

# 2. 코드
### 1) Python
```python
from itertools import permutations
from typing import List


class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        s = set()
        res = []

        for x in permutations(nums):
            key = "".join([str(a) for a in x])
            if key not in s:
                s.add(key)
                res.append(x)

        return res
```

### 2) Java
```java
import java.util.*;

class Solution {
    List<List<Integer>> res = new ArrayList<>();
    boolean[] check;
    int n;
    Set<String> s = new HashSet<>();
    public List<List<Integer>> permuteUnique(int[] nums) {
        n = nums.length;
        check = new boolean[n];

        dfs(new Stack<>(), 0, nums);

        return res;
    }

    public void dfs(Stack<Integer> l, int cnt, int[] nums) {
        if(cnt >= n) {
            List<Integer> cur = new ArrayList<>(l);
            StringBuilder key = new StringBuilder();
            for(int i=0; i<cur.size(); i++) {
                key.append(cur.get(i).toString());
            }
            if(!s.contains(key.toString())) {
                s.add(key.toString());
                res.add(cur);
            }
            return;
        }

        for(int i=0; i<n; i++) {
            if(!check[i]) {
                check[i] = true;
                l.push(nums[i]);
                dfs(l, cnt + 1, nums);
                l.pop();
                check[i] = false;
            }
        }
    }
}
```

### 3) JavaScript
```js
const permuteUnique = (nums) => {
    // 1. init
    const res = []
    const s = new Set()
    const n = nums.length
    const check = new Array(n).fill(false)

    // 2. dfs
    const dfs = (l, cnt) => {
        if(cnt >= n) {
            const key = l.join("")
            if(!s.has(key)) {
                s.add(key)
                res.push([...l])
            }
            return
        }

        for(let i=0; i<n; i++) {
            if(!check[i]){
                l.push(nums[i])
                check[i] = true
                dfs(l, cnt + 1)
                l.pop()
                check[i] = false
            }
        }
    }

    dfs([], 0)

    return res
};
```