# 1. 설명
- 두 문자 사이의 교집합이 없을 때 두 문자열 길이의 곱의 최대값을 구하세요


[문제 링크](https://leetcode.com/problems/maximum-product-of-word-lengths/)

# 2. 코드
### 1) Python
```python
from typing import List
from collections import Counter

class Solution:
    def maxProduct(self, words: List[str]) -> int:
        # 1. init
        n = len(words)
        w = [Counter(w) for w in words]
        res = 0

        # 2. loop
        for i in range(n):
            for j in range(i+1, n):
                a, b = w[i], w[j]
                if len(a & b) >= 1: continue

                res = max(res, sum(a.values()) * sum(b.values()))

        return res
```

### 2) Java
```java
class Solution {
    public int maxProduct(String[] words) {
        // 1. init
        int n = words.length;
        int[] w = new int[n];

        for(int i=0; i<n; i++) {
            String wo = words[i];
            int bit = 0;
            for(String c: wo.split("")) {
                int val = (int)c.charAt(0) - (int)"a".charAt(0);
                bit |= 1 << val;
            }
            w[i] = bit;
        }
        int res = 0;

        // 2. loop
        for(int i=0; i<n; i++) {
            for(int j=i+1; j<n; j++) {
                if((w[i] & w[j]) != 0) continue;

                res = Math.max(res, words[i].length() * words[j].length());
            }
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const maxProduct = (words) => {
    // 1. init
    const n = words.length
    const w = words.map(x => {
        let bit = 0
        x.split("").forEach(a => {
            const val = a.charCodeAt(0) - 'a'.charCodeAt(0)
            bit |= 1 << val
        })
        return bit
    })
    let res = 0

    // 2. loop
    for(let i=0; i<n; i++) {
        for(let j=i+1; j<n; j++) {
            const a = w[i]
            const b = w[j]
            if((a & b) !== 0) continue

            res = Math.max(res, words[i].length * words[j].length)
        }
    }

    return res
};
```

### 4) TypeScript
```ts
const maxProduct = (words: string[]): number => {
    // 1. init
    const n:number = words.length
    const w:number[] = words.map(x => {
        let bit:number = 0
        x.split("").forEach(a => {
            const val:number = a.charCodeAt(0) - 'a'.charCodeAt(0)
            bit |= 1 << val
        })
        return bit
    })
    let res:number = 0

    // 2. loop
    for(let i=0; i<n; i++) {
        for(let j=i+1; j<n; j++) {
            const a:number = w[i]
            const b:number = w[j]
            if((a & b) !== 0) continue

            res = Math.max(res, words[i].length * words[j].length)
        }
    }

    return res
};
```