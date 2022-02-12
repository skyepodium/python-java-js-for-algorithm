# 1. 설명
- 링크드 리스트의 중간 삭제


[문제 링크](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)

# 비고
러너 기법 - two pointer

# 2. 코드
### 1) python
```python
class Solution:
    def deleteMiddle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        # 1. init
        node = slow = fast = ListNode(None)
        node.next = head

        # 2. runner
        while fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next

        # 3. delete
        slow.next = slow.next.next

        return node.next
```

### 2) java
```java
class Solution {
    public ListNode deleteMiddle(ListNode head) {
        // 1. init
        ListNode node = new ListNode(-1);
        ListNode fast = node, slow = node;
        node.next = head;

        // 2. runner
        while(fast.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // 3. delete
        slow.next = slow.next.next;

        return node.next;
    }
}
```