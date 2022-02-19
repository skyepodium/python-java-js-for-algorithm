# 1. 설명
- 도미노 쌍의 개수를 구하세요.


[문제 링크](https://leetcode.com/problems/number-of-equivalent-domino-pairs/)

# 2. 코드
### 1) python
```python
class Solution:
    def numEquivDominoPairs(self, dominoes: List[List[int]]) -> int:
        return sum([x * (x - 1) // 2 for x in Counter([tuple(sorted(do)) for do in dominoes]).values()])
```


### 2) java
```java
class Solution {
    public int numEquivDominoPairs(int[][] dominoes) {
        // 1. init
        Map<Integer, Integer> m = new HashMap<>();
        int res = 0;

        // 2. counter
        for(int[] d: dominoes) {
            int num = Math.max(d[0], d[1]) * 10 + Math.min(d[0], d[1]);
            m.put(num, m.getOrDefault(num, 0) + 1);
        }

        // 3. for loop
        for(Integer c: m.values()) {
            res += c * (c - 1) / 2;
        }

        return res;
    }
}
```