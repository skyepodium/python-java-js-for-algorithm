# 1. 설명
- 빈도가 가장 높은 순서대로 k개만 반환하세요



[문제 링크](https://leetcode.com/problems/top-k-frequent-elements/)

# 2. 코드
### 1) Python
```python
class Solution:
    def topKFrequent(self, words: List[str], k: int) -> List[str]:
        return [a for a, b in sorted(Counter(words).items(), key=lambda x: -x[1])][:k]
```

### 2) Java
```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> m = new HashMap<>();

        Arrays.stream(nums).forEach(x -> m.put(x, m.getOrDefault(x, 0) + 1));

        return Arrays.copyOfRange(m.entrySet().stream().sorted((a, b) -> b.getValue() - a.getValue())
                .mapToInt(Map.Entry::getKey)
                .toArray(), 0, k);
    }
}
```

### 3) JavaScript
```js
const topKFrequent = (nums, k) => {
    const m = new Map()

    nums.forEach(x => {
        if(m.has(x)) m.set(x, m.get(x) + 1)
        else m.set(x, 1)
    })

    return [...m.entries()]
        .sort((a, b) => b[1] - a[1])
        .map(x => x[0])
        .slice(0, k)
};
```

### 4) C++
```cpp
struct cmp {
    bool operator()(const pair<int, int>& a, const pair<int, int>& b) {
        return a.second > b.second;
    }
};

class Solution {
   public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        // 1. init
        unordered_map<int, int> m;

        // 2. count
        for (auto num : nums) {
            m[num]++;
        }

        // 3. sort
        vector<pair<int, int>> v(m.begin(), m.end());
        sort(v.begin(), v.end(), cmp());

        // 4. return
        vector<int> res;
        for (int i = 0; i < k; i++) {
            res.push_back(v[i].first);
        }

        return res;
    }
};
```