# 1. 설명
- 두 링크드 리스트를 더한 합을 링크드 리스트로 반환하세요.


[문제 링크](https://leetcode.com/problems/add-two-numbers/)

# 2. 코드
### 1) python
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:

        res = node = ListNode(0)

        carry = 0
        while l1 or l2 or carry:
            sum_val = 0
            if l1:
                sum_val += l1.val
                l1 = l1.next

            if l2:
                sum_val += l2.val
                l2 = l2.next

            carry, val = divmod(sum_val + carry, 10)

            node.next = ListNode(val)
            node = node.next

        return res.next  
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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {

        // 1. init
        ListNode node = new ListNode(0);
        ListNode res = node;

        int carry = 0;
        while(l1 != null || l2 != null || carry > 0) {
            int sumVal = 0;

            if(l1 != null) {
                sumVal += l1.val;
                l1 = l1.next;
            }

            if(l2 != null) {
                sumVal += l2.val;
                l2 = l2.next;
            }

            int val = (sumVal + carry) % 10;
            carry = (sumVal + carry) / 10;

            node.next = new ListNode(val);;
            node = node.next;
        }

        return res.next;
    }
}
```