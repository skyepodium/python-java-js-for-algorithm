# 1. 설명
- 두개를 더해서 target이 되는 인덱스를 반환하세요

- 배열의 길이 1 <= n <= 10만



[문제 링크](https://leetcode.com/problems/two-sum/)

# 2. 코드
## O(n) - map
### 1) python
```python
class Solution:
    def twoSum(self, nums: list[int], target: int) -> list[int]:
        # 1. init
        d = {}

        # 2. loop
        for idx, num in enumerate(nums):
            remain = target - num
            if remain in d:
                return [d[remain], idx]
            else:
                d[num] = idx
```
### 2) java
````java
lass Solution {
    public int[] twoSum(int[] nums, int target) {
        // 1. init
        int[] res = new int[2];
        Map<Integer, Integer> m = new HashMap<>();

        // 2. loop
        for(int i=0; i<nums.length; i++) {
            int cur = nums[i];
            int remain = target - cur;
            if(m.containsKey(remain)) {
                int idx = m.get(remain);
                res[0] = idx;
                res[1] = i;
                break;
            }
            else {
                m.put(cur, i);
            }
        }

        return res;
    }
}
````

## O(nlogn) - 정렬
### 1) python
```python
class Solution:
    def twoSum(self, nums: list[int], target: int) -> list[int]:

        # 1. 리스트 컴프리헨션으로 (인덱스, 값) 튜플 리스트 생성
        num_list = [(idx, num) for idx, num in enumerate(nums)]

        # 2. 값 기준 정렬
        num_list.sort(key=lambda x: x[1])

        # 3. 투포인터
        l = 0
        r = len(num_list) - 1

        while l < r:
            sum_val = num_list[l][1] + num_list[r][1]
            # 1) 값이 크면 오른쪽 포인터 왼쪽으로
            if sum_val > target:
                r -= 1
            # 2) 값이 작으면 왼쪽 포인터 오른쪽으로
            elif sum_val < target:
                l += 1
            # 3) 값이 같으면, 인덱스 반환
            else:
                return num_list[l][0], num_list[r][0]
```

### 2) java
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        // 1. init
        int[] res = new int[2];
        List<Info> numList = new ArrayList<>();
        for(int i=0; i<nums.length; i++) {
            numList.add(new Info(nums[i], i));
        }

        // 2. sort
        numList.sort(Comparator.comparingInt(a -> a.num));

        // 3. two pointer
        int l = 0;
        int r = nums.length - 1;
        while(l < r) {
            int cur = numList.get(l).num + numList.get(r).num;

            if(cur < target) {
                l++;
            }
            else if(cur > target) {
                r--;
            }
            else {
                res[0] = numList.get(l).idx;
                res[1] = numList.get(r).idx;
                break;
            }
        }

        return res;
    }
}

class Info {
    int num;
    int idx;

    public Info(int num, int idx) {
        this.num = num;
        this.idx = idx;
    }
}
```