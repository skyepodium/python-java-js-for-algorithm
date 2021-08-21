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
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {

        if((l1 == null) || (l2 != null && l1.val > l2.val)) {
            ListNode temp = null;
            temp = l1;
            l1 = l2;
            l2 = temp;
        }

        if(l1 != null) {
            l1.next = this.mergeTwoLists(l1.next, l2);
        }

        return l1;
    }
}
```