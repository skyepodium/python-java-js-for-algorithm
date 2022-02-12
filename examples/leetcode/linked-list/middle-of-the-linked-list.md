# 1. 설명
- 링크드 리스트의 중간 노드 부터 반환


[문제 링크](https://leetcode.com/problems/middle-of-the-linked-list/)

# 비고
러너 기법

# 2. 코드
### 1) python
```python
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        # 1. init
        slow = fast = head

        # 2. runner
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next

        return slow
```

### 2) java
```java
class Solution {
    public ListNode middleNode(ListNode head) {
        // 1. init
        ListNode fast = head, slow = head;

        // 2. runner
        while(fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        return slow;
    }
}
```