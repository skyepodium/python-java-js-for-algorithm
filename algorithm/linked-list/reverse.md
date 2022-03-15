[leetcode - reverse-linked-list](https://leetcode.com/problems/reverse-linked-list/) - 뒤집기

# 1. python
```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        # 1. init
        rev = None

        # 2. loop
        while head:
            # 뒤집는다.
            rev, rev.next, head = head, rev, head.next

            '''
            원래 방식 - 순서 지켜야한다.
            temp = head
            head = head.next
            temp.next = rev
            rev = temp
            '''

        return rev
```

# 2. java
```java
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