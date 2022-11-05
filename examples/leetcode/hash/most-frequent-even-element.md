# 1. 설명
- 빈도가 가장 큰 짝수를 반환하세요
- 빈도수가 같으면 더 작은수
- 짝수가 없으면 -1 반환

[문제 링크](https://leetcode.com/problems/missing-number/)

# 2. 코드
### 1) python
```python
class Solution:
    def mostFrequentEven(self, nums: List[int]) -> int:
        # 1. init
        d = defaultdict(int)

        # 2. loop
        for num in nums:
            if num & 1 == 1: continue
            d[num] += 1

        # 3. sort
        r = sorted([(key, val) for key, val in d.items()], key=lambda x: (-x[1], x[0]))

        # 4. return
        return r[0][0] if len(r) > 0 else -1
```

### 2) java
```java
class Solution {
    public int mostFrequentEven(int[] nums) {
        // 1. init
        HashMap<Integer, Integer> m = new HashMap<>();

        // 2. count
        for(int num: nums) {
            if((num & 1) == 1) continue;
            m.put(num, m.getOrDefault(num, 0) + 1);
        }

        // 3. sort
        List<Integer> l = m.entrySet().stream().sorted((a, b) -> {
            if(Objects.equals(a.getValue(), b.getValue())) return a.getKey() - b.getKey();
            return b.getValue() - a.getValue();
        }).map(Map.Entry::getKey).collect(Collectors.toList());

        // 4. return
        return l.size() == 0 ? -1 : l.get(0);
    }
}
```

### 3) JavaScript
```js
const mostFrequentEven = (nums) => {
    // 1. init
    const m = new Map();

    // 2. loop
    nums.forEach((num) => {
        if (num % 2 === 0) {
            m.set(num, (m.get(num) || 0) + 1);
        }
    })

    // 3. sort
    const sorted = [...m.entries()].sort((a, b) => {
        return a[1] === b[1] ? a[0] - b[0] : b[1] - a[1]
    })

    // 4. return
    return sorted.length > 0 ? sorted[0][0] : -1
};
```

### 4) C++
```cpp
struct cmp {
    bool operator()(const pair<int, int>& a, const pair<int, int>& b) {
        if (a.second == b.second) {
            return a.first < b.first;
        }

        return a.second > b.second;
    }
};

class Solution {
   public:
    int mostFrequentEven(vector<int>& nums) {
        // 1. init
        unordered_map<int, int> map;

        // 2. count
        for (auto num : nums) {
            if (num & 1 == 1) continue;
            map[num]++;
        }

        // 3. sort
        vector<pair<int, int>> v(map.begin(), map.end());
        sort(v.begin(), v.end(), cmp());

        // 4. return
        return v.size() > 0 ? v[0].first : -1;
    }
};
```