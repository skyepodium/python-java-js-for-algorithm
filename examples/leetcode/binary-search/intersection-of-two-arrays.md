# 1. 설명
- 두 배열의 교집합을 반환하세요.

[문제 링크](https://leetcode.com/problems/intersection-of-two-arrays/)

# 2. 코드
### 1) python
```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:

        # 1. init
        nums1.sort()
        nums2.sort()
        answer = []
        
        # 2. binary_search
        def binary_search(l, r, target):
            while l <= r:
                mid = l + (r-l) // 2
                if nums2[mid] < target:
                    l = mid + 1
                elif nums2[mid] > target:
                    r = mid - 1
                else:
                    return mid
            return -1
        
        # 3. loop
        for i in range(0, len(nums1)):
            if i > 0 and nums1[i] == nums1[i-1]:
                continue
                
            val = nums1[i]
            
            if binary_search(0, len(nums2) -1, val) != -1:
                answer.append(val)
        
        return answer
```

### 2) java
```java
import java.util.ArrayList;
import java.util.Arrays;

class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        // 1. init
        int size1 = nums1.length;
        int size2 = nums2.length;
        ArrayList<Integer> res = new ArrayList<>();
        Arrays.sort(nums1);
        Arrays.sort(nums2);

        for(int i=0; i<size1; i++) {
            if(i >= 1 && nums1[i] == nums1[i-1]) {
                continue;
            }

            int val = nums1[i];

            if(binarySearch(0, size2-1, nums2, val) != -1) {
                res.add(val);
            }
        }
        int resSize = res.size();
        int[] result = new int[resSize];
        for(int i=0; i<resSize; i++) {
            result[i] = res.get(i);
        }

        return result;
    }

    public int binarySearch(int l, int r, int[] nums, int target) {
        while(l <= r) {
            int mid = l + (r-l) / 2;

            if(nums[mid] < target) {
                l = mid + 1;
            }
            else if(nums[mid] > target) {
                r = mid - 1;
            }
            else{
                return mid;
            }
        }
        return -1;
    }
}
```