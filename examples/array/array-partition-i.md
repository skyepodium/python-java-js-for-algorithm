# 1. 설명
- n개의 페어에서 min값의 총합의 최대값을 반환하세요.

배열의 길이 1 <= n <= 1만



[문제 링크](https://leetcode.com/problems/array-partition-i/submissions/)

# 2. 코드
### 1) python
```python
class Solution:
    def arrayPairSum(self, nums: list[int]) -> int:

        # 1. 정렬
        # 2. 정렬된 배열에서 0부터 2칸씩 건너 뛰어서 짝수번째 합 계산
        return sum(sorted(nums)[::2])
```

### 2) java
```java
class Solution {
    public int arrayPairSum(int[] nums) {
        // 1. 정렬
        Arrays.sort(nums);

        int result = 0;
        int size = nums.length;

        // 2. 정렬된 결과에서 짝수번째 합 계산
        for(int i=0; i<size; i=i+2){
            result += nums[i];
        }
        return result;
    }
}
```