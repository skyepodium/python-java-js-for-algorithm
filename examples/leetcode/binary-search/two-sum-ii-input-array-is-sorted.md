# 1. 설명
- 오름차순으로 정렬된 배열에서 두개를 선택해서 더했을때 target이 되는 경우 인덱스 2개를 반환하세요.

[문제 링크](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

# 비고
- 투 포인터 O(N)
- 이진 탐색 O(NlogN)

투 포인터가 더 빠르다. 다만, 책에서는 bisect, 슬라이싱 예제를 보여주기 위해 이진 탐색을 사용했다.

# 2. 코드
### 1) python
```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        # 0. init
        size = len(numbers)

        # 1. binary_search
        def binary_search(l, r, remain):
            while l <= r:
                mid = l + (r - l) // 2

                if numbers[mid] > remain:
                    r = mid - 1
                elif numbers[mid] < remain:
                    l = mid + 1
                else:
                    return mid
            return -1

        # 2. loop
        for i in range(size - 1):
            l = i + 1
            r = size - 1

            res = binary_search(l, r, target - numbers[i])
            if res != -1:
                return [i + 1, res + 1]
```

### 2) java
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        // 1. init
        int size = numbers.length;
        int[] answer= {0, 0};

        for(int i=0; i<size-1; i++) {
            int l = i+1;
            int r = size-1;
            int remain = target - numbers[i];

            while(l<=r) {
                int mid = l + (r-l) / 2;
                if(numbers[mid] < remain) {
                    l = mid + 1;
                }
                else if(numbers[mid] > remain) {
                    r = mid - 1;
                }
                else {
                    answer[0] = i+1;
                    answer[1] = mid + 1;
                    return answer;
                }
            }
        }
        return answer;
    }
}
```