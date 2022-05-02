# 1. 설명
짝수 앞으로 홀수 뒤로 정렬, 순서 관계없음

[문제 링크](https://leetcode.com/problems/sort-array-by-parity/)

# 2. 코드
### 1) Python
```python
class Solution:
    def sortArrayByParity(self, nums: List[int]) -> List[int]:
        
        return sorted(nums, key=lambda x: 0 if x % 2 == 0 else 1)
```