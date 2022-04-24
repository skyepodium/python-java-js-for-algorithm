# 1. 설명
H-index 를 구하세요

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42747)


# 2. 코드
### 1) Python
```python
def solution(citations):
    # 1. init
    res = 0
    max_val = max(citations)
    n = len(citations)

    # 2. sort
    citations.sort()

    # 3. lower_bound
    def lower_bound(s, e, target):
        while s < e:
            mid = s + (e - s) // 2
            if citations[mid] < target:
                s = mid + 1
            else:
                e = mid
        return e

    # 4. loop
    for i in range(max_val+1):
        idx = lower_bound(0, n, i)
        upper = n - idx
        if upper >= i:
            res = max(res, i)

    return res
```

### 2) Java
```java
import java.util.Arrays;

class Solution {
    public int solution(int[] citations) {
        // 1. int
        int res = 0;
        int maxVal = Arrays.stream(citations).max().getAsInt();
        int n = citations.length;

        // 2. sort
        citations = Arrays.stream(citations).sorted().toArray();

        // 3. lower bound
        for(int i=0; i<=maxVal; i++) {
            int idx = lowerBound(0, n, i, citations);
            int upper = n - idx;
            if(upper >= i) res = Math.max(res, i);
        }

        return res;
    }

    public int lowerBound(int s, int e, int target, int[] c) {
        while(s < e) {
            int mid = s + (e - s) / 2;
            if(c[mid] < target) s = mid + 1;
            else e = mid;
        }
        return e;
    }
}
```

### 3) JavaScript
```js
const solution = citations => {
    // 1. init
    let res = 0
    const maxVal = Math.max(...citations)
    const n = citations.length

    // 2. sort
    citations.sort((a, b ) => a - b)

    // 3. lowerBound
    const lowerBound = (s, e, target) => {
        while(s < e) {
            const mid = s + ~~((e-s) / 2)
            if(citations[mid] < target) s = mid + 1
            else e = mid
        }
        return e
    }

    // 4. loop
    for(let i=0; i<=maxVal; i++) {
        const idx = lowerBound(0, n, i)
        const upper = n - idx
        if(upper >= i) res = Math.max(res, i)
    }

    return res
}
```