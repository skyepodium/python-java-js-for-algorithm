# 1. 설명
- 단 1개의 숫자 빼고 2번씩 등장한다
- 1번 등장하는 숫자를 찾으세요.



[문제 링크](https://leetcode.com/problems/single-number/)

# XOR
처음에는 python Counter로 풀었는데, discussion을 봤다.

1개, 2개 등장하는 특성을 알면 XOR을 적용할 수 있다.

### XOR 특성
같은것을 2번 xor 연산하면 복원된다.
a ^ b = c
c ^ b = a

# 2. 코드
### 1) python
```python
class Solution:
    def singleNumber(self, nums: list[int]) -> int:
        # 1. init
        res = nums[0]

        # 2. xor
        for i in range(1, len(nums)):
            res ^= nums[i]
            print(nums[i], res)

        return res
```

### 2) java
```java
class Solution {
    public int singleNumber(int[] nums) {
        // 1. init
        int res = nums[0];
        int size = nums.length;

        // 2. xor
        for(int i=1; i<size; i++) {
            res ^= nums[i];
            System.out.println(nums[i] + " " + res);
        }

        return res;
    }
}
```