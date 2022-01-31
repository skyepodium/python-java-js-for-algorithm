# 1. 설명
- 빈도가 가장 높은 순서대로 k개만 반환하세요



[문제 링크](https://leetcode.com/problems/top-k-frequent-elements/)

# 2. 코드
### 1) python
```python
class Solution:
    def topKFrequent(self, words: List[str], k: int) -> List[str]:
        # 1. init
        res = []
        cnt = 0

        # 2. result
        for x in sorted(Counter(words).items(), key=lambda x: -x[1]):
            if cnt >= k: break
            res.append(x[0])
            cnt += 1

        return res
```

### 2) java
```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        // 1. init
        int[] res = new int[k];
        Map<Integer, Integer> m = new HashMap<>();
        List<Info> numList = new ArrayList<>();
        int idx = 0;

        // 2. count
        Arrays.stream(nums).forEach(x -> {
            if(m.containsKey(x)) m.put(x, m.get(x) + 1);
            else m.put(x, 1);
        });

        // 3. to list
        m.keySet().stream().forEach(x -> {
            numList.add(new Info(x, m.get(x)));
        });

        // 4. sort
        numList.sort((a, b) -> b.cnt - a.cnt);

        // 5. result
        for(Info info: numList) {
            if(idx >= k) break;
            res[idx] = info.num;
            idx++;
        }

        return res;
    }
}

class Info {
    int num;
    int cnt;
    public Info (int num, int cnt) {
        this.num = num;
        this.cnt = cnt;
    }
}
```