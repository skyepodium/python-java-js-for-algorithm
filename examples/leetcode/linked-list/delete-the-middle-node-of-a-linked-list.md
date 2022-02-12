# 1. 설명
- 링크드 리스트의 중간 삭제


[문제 링크](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)

# 비고
러너 기법

# 2. 코드
### 1) python
```python
class Solution:
    def deleteMiddle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        # 1. init
        fast = slow = head
        s = []

        # 2. runner
        while fast and fast.next:
            s.append(slow.val)
            slow = slow.next
            fast = fast.next.next

        # 3. stack
        res = slow.next
        while s:
            res = ListNode(s.pop(), res)

        return res
```

### 2) java
```java
class Solution {
    public ListNode deleteMiddle(ListNode head) {
        // 1. init
        ListNode fast = head, slow = head;
        Stack<Integer> s = new Stack<>();

        // 2. runner
        while(fast != null && fast.next != null) {
            s.add(slow.val);
            slow = slow.next;
            fast = fast.next.next;
        }

        // 3. stack
        ListNode res = slow.next;
        while(!s.empty()) {
            res = new ListNode(s.pop(), res);
        }

        return res;
    }
}
```