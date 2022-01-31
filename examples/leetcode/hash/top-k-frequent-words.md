# 1. 설명
- 빈도가 가장 높은 순서대로 k개만 반환하세요



[문제 링크](https://leetcode.com/problems/top-k-frequent-words/)

# 2. 코드
### 1) python
```python
class Solution:
    def topKFrequent(self, words: List[str], k: int) -> List[str]:
        # 1. init
        res = []
        cnt = 0

        # 2. result
        for x in sorted(Counter(words).items(), key=lambda x: (-x[1], x[0])):
            if cnt >= k: break
            res.append(x[0])
            cnt += 1

        return res
```

### 2) java
```java
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
        // 1. init
        List<String> res = new ArrayList<>();
        Map<String, Integer> m = new HashMap<>();
        List<Info> wList = new ArrayList<>();
        int idx = 0;

        // 2. counter
        Arrays.stream(words).forEach(x -> {
            if(m.containsKey(x)) m.put(x, m.get(x) + 1);
            else m.put(x, 1);
        });

        // 3. map to list
        m.keySet().forEach(x -> {
            wList.add(new Info(x, m.get(x)));
        });

        // 4. sort
        wList.sort((a, b) -> {
            if(a.cnt == b.cnt) return a.w.compareTo(b.w);
            else return b.cnt - a.cnt;
        });

        // 5. loop
        for(Info info: wList) {
            if(idx >= k) break;
            res.add(info.w);
            idx++;
        }

        return res;
    }
}

class Info {
    String w;
    int cnt;
    public Info(String w, int cnt) {
        this.w = w;
        this.cnt = cnt;
    }
}
```