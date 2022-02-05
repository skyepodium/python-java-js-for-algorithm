# 1. 설명
- jewels에 포함된 Stones 요소의 개수를 구하세요.


[문제 링크](https://leetcode.com/problems/jewels-and-stones/)

# 2. 코드
### 1) python
#### 해시맵
```python
class Solution:
    def numJewelsInStones(self, jewels: str, stones: str) -> int:
        # 1. init
        c = Counter(stones)
        res = 0

        # 2. loop
        for j in jewels:
            res += c[j]

        return res
```

#### 파이써닉 한 방법
```python
class Solution:
    def numJewelsInStones(self, jewels: str, stones: str) -> int:
        return sum([s in jewels for s in stones])
```

### 2) java
#### 해시맵
```java
class Solution {
    public int numJewelsInStones(String jewels, String stones) {
        // 1. init
        int res = 0;
        Map<Character, Integer> m = new HashMap<>();

        // 2. make counter
        for(int i=0; i<stones.length(); i++) {
            Character c = stones.charAt(i);
            if(m.containsKey(c)) m.put(c, m.get(c) + 1);
            else m.put(c, 1);
        }

        // 3. check
        for(int i=0; i<jewels.length(); i++) {
            Character j = jewels.charAt(i);
            if(m.containsKey(j)) res += m.get(j);
        }

        return res;
    }
}
```

#### 문자열 사용
```java
class Solution {
    public int numJewelsInStones(String jewels, String stones) {
        int cnt = 0;

        for(int i=0; i<stones.length(); i++) {
            String cur = stones.charAt(i) + "";

            if(jewels.contains(cur)) cnt++;
        }

        return cnt;
    }
}
```