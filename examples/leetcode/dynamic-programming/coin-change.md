# 1. 설명
- 동전 교환 최소 개수를 구하세요

[문제 링크](https://leetcode.com/problems/coin-change/)

# 2. 코드
### 1) Python
```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        # 1. init
        max_int = amount + 1
        d = [max_int for _ in range(max_int)]
        coins = [c for c in coins if c <= amount]
        d[0] = 0

        # 2. bottom up
        for i in range(0, max_int):
            for c in coins:
                if i-c >= 0:
                    d[i] = min(d[i], d[i-c] + 1)

        return d[amount] if d[amount] <= amount else -1
```

### 2) Java
```java
class Solution {
    public int coinChange(int[] coins, int amount) {
        // 1. init
        int[] d = new int[amount+1];
        for(int i=1; i<=amount; i++) d[i] = amount + 1;
        d[0] = 0;

        // 2. bottom up
        for(int i=1; i<=amount; i++) {
            for(int c: coins) {
                if(i-c>=0) {
                    d[i] = Math.min(d[i], d[i-c] + 1);
                }
            }
        }

        return d[amount] <= amount ? d[amount] : -1;
    }
}
```

### 3) JavaScript
```js
const coinChange = (coins, amount) => {
    // 1. init
    const d = Array.from(new Array(amount+1).fill(amount+1))
    d[0] = 0

    // 2. bottom up
    for(let i=1; i<=amount; i++) {
        for(const c of coins) {
            if(i-c < 0) continue

            d[i] = Math.min(d[i], d[i-c] + 1)
        }
    }

    return d[amount] <= amount ? d[amount] : -1
};
```

### 4) TypeScript
```ts
const coinChange = (coins: number[], amount: number): number => {
    // 1. init
    const d:number[] = Array.from(new Array(amount+1).fill(amount+1))
    d[0] = 0

    // 2. bottom up
    for(let i=1; i<=amount; i++) {
        for(const c of coins) {
            if(i-c < 0) continue

            d[i] = Math.min(d[i], d[i-c] + 1)
        }
    }

    return d[amount] <= amount ? d[amount] : -1
};
```