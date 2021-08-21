# 1. 설명
- 링크드 리스트를 뒤집으세요.


[문제 링크](https://leetcode.com/problems/reverse-linked-list/)

# 2. 코드
### 1) python
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        # 1. init
        rev = None

        # 2. loop
        while head:
            rev, rev.next, head = head, rev, head.next

        return rev 
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
    public ListNode reverseList(ListNode head) {
        // 1. init
        ListNode rev = null;

        // 2. loop
        while(head != null) {
            ListNode temp = head;
            head = head.next;
            temp.next = rev;
            rev = temp;
        }

        return rev;
    }
}
```