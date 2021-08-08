# 1. 설명
- 높이가 리스트로 주어졌을때 빗물이 얼마나 쌓일지를 계산하세요.

배열의 길이 1 <= n <= 20만



[문제 링크](https://leetcode.com/problems/trapping-rain-water/)

# 2. 코드
### 1) python
```python
class Solution:
    def trap(self, height: list[int]) -> int:

        result = 0;

        # 1. 왼쪽, 오른쪽 최대 높이 저장할 변수 생성
        l, r = 0, len(height) - 1
        left_max, right_max = height[l], height[r]

        while l <= r:
            # 2. 투 포인터 왼쪽, 오른쪽 최대값 갱신
            left_max = max(left_max, height[l])
            right_max = max(right_max, height[r])

            # 3. 최대 높이를 향해 투 포인터 이동
            if left_max <= right_max:
                result += left_max - height[l]
                l += 1
            else:
                result += right_max - height[r]
                r -= 1

        return result
```

### 2) java
```java
class Solution {
    public int trap(int[] height) {

        int result = 0;

        // 1. 왼쪽, 오른쪽 최대 높이를 저장할 변수 생성
        int l = 0;
        int r = height.length - 1;
        int leftMax = height[l];
        int rightMax = height[r];

        while(l <= r) {
            // 2. 투 포인터 왼쪽, 오른쪽 최대값 갱신
            leftMax = Math.max(leftMax, height[l]);
            rightMax = Math.max(rightMax, height[r]);

            // 3. 최대 높이를 향해 투 포인터 이동
            if(leftMax <= rightMax) {
                result += leftMax - height[l];
                l++;
            }
            else {
                result += rightMax - height[r];
                r--;
            }
        }

        return result;
    }
}
```