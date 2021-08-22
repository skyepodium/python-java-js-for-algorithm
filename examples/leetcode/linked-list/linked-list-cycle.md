# 1. 설명
- 링크드 리스트의 사이클 여부를 반환하세요.


[문제 링크](https://leetcode.com/problems/linked-list-cycle/)

# 비고
러너 기법을 사용하자!!!

# 2. 코드
### 1) python
```python
class Solution:
    def hasCycle(self, head: ListNode) -> bool:
        if not head:
            return False

        slow = fast = head

        while fast and fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next

            if slow == fast:
                return True

        return False
```

### 2) java
```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;

        while(fast != null && fast.next != null && fast.next.next != null) {
            fast = fast.next.next;
            slow = slow.next;

            if(fast == slow) {
                return true;
            }
        }
        return false;
    }
}
```