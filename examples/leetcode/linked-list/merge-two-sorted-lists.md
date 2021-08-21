# 1. 설명
- 정렬된 두 링크드 리스트를 정렬된 상태로 병합하세요.


[문제 링크](https://leetcode.com/problems/merge-two-sorted-lists/)

# 2. 코드
### 1) python
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        
        if (not l1) or (l2 and l1.val > l2.val):
            l1, l2 = l2, l1

        if l1:
            l1.next = self.mergeTwoLists(l1.next, l2)

        return l1    
```

### 2) java
```java
class Solution {
    public int maxSubArray(int[] nums) {
        // 1. init
        int size = nums.length;
        int[] d = new int[size];
        int res = d[0] = nums[0];
        
        // 2. tabulation
        for(int i=1; i<size; i++) {
            d[i] = max(nums[i], d[i-1] + nums[i]);
            
            res = max(res, d[i]);
        }
        
        return res;
    }
    
    public int max(int a, int b) {
        return a > b ? a : b;
    }
}
```