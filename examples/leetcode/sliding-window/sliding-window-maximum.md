# 1. 설명
슬라이딩 윈도우에 포함된 수의 최대값을 반환하세요.


[문제 링크](https://leetcode.com/problems/sliding-window-maximum/)

책에서는 큐를 사용하라고 되어있는데 시간 초과가 발생합니다.

덱을 사용했습니다.

덱의 가장앞에 최대값을 유지하는 방법으로 진행했습니다.

# 2. 코드
### 1) python
```python
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        # 1. init
        res = []
        n = len(nums)
        dq = deque()

        # 2. loop
        for i in range(n):
            # 1) over size
            if dq and dq[0] <= i - k: dq.popleft()

            # 2) make front biggest
            while dq and nums[dq[-1]] < nums[i]: dq.pop()

            # 3) insert
            dq.append(i)

            # 4) update
            if i >= k - 1:
                res.append(nums[dq[0]])

        return res
```

### 2) java
```java
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        // 1. init
        int n = nums.length;
        Deque<Integer> dq = new ArrayDeque<>();
        int[] res = new int[n - k + 1];
        int idx = 0;

        // 2. loop
        for(int i=0; i<n; i++) {
            // 1) over size
            if(!dq.isEmpty() && dq.peekFirst() <= i - k) dq.pollFirst();

            // 2) make front biggest
            while(!dq.isEmpty() && nums[dq.peekLast()] < nums[i]) dq.pollLast();

            // 3) insert dq
            dq.add(i);

            // 4) update
            if(i >= k - 1) res[idx++] = nums[dq.peekFirst()];
        }

        return res;
    }
}
```