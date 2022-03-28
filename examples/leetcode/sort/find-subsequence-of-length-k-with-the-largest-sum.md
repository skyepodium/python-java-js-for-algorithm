# 1. 설명
합이 가장 큰 배열 인덱스 순으로 반환

[문제 링크](https://leetcode.com/problems/find-subsequence-of-length-k-with-the-largest-sum/)

# 2. 코드
### 1) python
```python
class Solution:
    def maxSubsequence(self, nums: List[int], k: int) -> List[int]:

        a = sorted([(idx, val) for idx, val in enumerate(nums)], key=lambda x: -x[1])[:k]

        return [x[1] for x in sorted(a, key=lambda x: x[0])]
```

### 2) java
```java
import java.util.ArrayList;
import java.util.Comparator;
import java.util.List;

class Solution {
    public int[] maxSubsequence(int[] nums, int k) {
        List<Info> l = new ArrayList<>();
        int idx = 0;
        for(int n: nums) {
            l.add(new Info(idx++, n));
        }

        l.sort((a, b) -> b.val - a.val);

        l = l.subList(0, k);
        
        l.sort(Comparator.comparingInt(a -> a.idx));

        return l.stream().mapToInt(x -> x.val).toArray();
    }
}

class Info {
    public int idx;
    public int val;
    public Info(int idx, int val) {
        this.idx = idx;
        this.val = val;
    }
}
```

### 3) JavaScript
```js
const maxSubsequence = (nums, k) => {
    
    return nums.map((x, idx) => [x, idx])
                .sort((a, b) => b[0] - a[0])
                .slice(0, k)
                .sort((a, b) => a[1] - b[1])
                .map(x => x[0])
};
```