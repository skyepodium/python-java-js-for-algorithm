# 1. 설명
- 자신을 제외한 곱셈의 결과를 반환하세요
- 나눗셈을 사용할 수 없습니다.

배열의 길이 1 <= n <= 10만



[문제 링크](https://leetcode.com/problems/product-of-array-except-self/)

# 2. 코드
### 1) python
```python
class Solution:
    def productExceptSelf(self, nums: list[int]) -> list[int]:

        result = []
        size = len(nums)

        # 1. 자기 자신을 제외한 왼쪽 누적곱을 저장한다.
        base = 1
        for i in range(0, size):
            result.append(base)
            base *= nums[i]

        # 2. 1번 결과에 자신을 제외한 오른쪽 누적곱을 곱해준다.
        base = 1
        for i in range(size - 1, -1, -1):
            result[i] = result[i] * base
            base *= nums[i]

        return result
```

### 2) java
```java
class Solution {
    public int[] productExceptSelf(int[] nums) {

        int size = nums.length;
        int[] result = new int[size];
        int base = 0;

        // 1. 자신을 제외한 왼쪽의 누적곱을 저장한다.
        base = 1;
        for(int i=0; i<size; i++) {
            result[i] = base;
            base *= nums[i];
        }

        // 2. 1번 결과에 자신을 제외한 오른쪽 누적곱을 곱해준다.
        base = 1;
        for(int i=size-1; i>=0; i--) {
            result[i] = result[i] * base;
            base *= nums[i];
        }

        return result;
    }
}
```