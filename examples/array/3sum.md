# 1. 설명
- 3개의 서로 다른 값을 더해서 0이되는 경우를 모두 구하세요.
- 중복된 경우는 없어야합니다.

배열의 길이 1 <= n <= 3000



[문제 링크](https://leetcode.com/problems/3sum/)

# 2. 코드
### 1) python
```python
class Solution:
    def threeSum(self, nums: list[int]) -> list[list[int]]:

        # 1. 정렬
        nums.sort()

        result = []
        size = len(nums)

        # 2. 인덱스 1개 고정
        for i in range(size - 2):

            # 3. 방금전에 계산한 값과 같으면 패스
            if i > 0 and nums[i] == nums[i-1]:
                continue

            l = i + 1
            r = size - 1

            # 4. 투 포인터 양끝에서 좁혀가며 계산
            while l < r:
                sum_val = nums[i] + nums[l] + nums[r]

                if sum_val > 0:
                    r -= 1
                elif sum_val < 0:
                    l += 1
                else:
                    result.append([nums[i], nums[l], nums[r]])

                    # 5. 중복값 제거
                    while l < r and nums[l] == nums[l+1]:
                        l += 1

                    # 6. 중복값 제거
                    while l < r and nums[r] == nums[r-1]:
                        r -= 1

                    l += 1
                    r -= 1

        return result
```

### 2) java
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {

        List<List<Integer>> result = new ArrayList<>();

        // 1. 정렬
        Arrays.sort(nums);

        // 2. 인덱스 1개 고정
        int size = nums.length;
        for(int i=0; i<size-2; i++) {

            // 3. 방금전 계산한 값과 같으면 패스
            if(i > 0 && nums[i] == nums[i-1]) continue;

            int l = i+1;
            int r = size - 1;

            // 4. 투 포인터 양끝에서 좁혀가며 계산
            while(l < r) {
                int sumVal = nums[l] + nums[r] + nums[i];

                if(sumVal > 0) {
                    r--;
                }
                else if(sumVal < 0) {
                    l++;
                }
                else {
                    List<Integer> triplet = new ArrayList<>(Arrays.asList(nums[l], nums[r], nums[i]));
                    result.add(triplet);

                    // 5. 중복값 제거
                    while(l < r && nums[l] == nums[l+1]) l++;
                    // 6. 중복값 제거
                    while(l < r && nums[r] == nums[r-1]) r--;

                    l++;
                    r--;
                }
            }
        }

        return result;
    }
}
```