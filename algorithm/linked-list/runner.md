[leetcode - linked-list-cycle](https://leetcode.com/problems/linked-list-cycle/) - 러너

# 1. python
```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        # 1. init
        fast = slow = head

        # 2. runner
        '''
        fast는 2칸씩, slow 1칸씩 이동
        fast가 끝에 도달하면, slow는 링크드 리스트 중앙에 위치한다.
        fast가 2칸 이동 할 수 있을 때 까지 탐색한다.
        '''
        while fast and fast.next:
            slow, fast = slow.next, fast.next.next

            if slow == fast:
                return True

        return False
```

# 2. java
```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        // 1. init
        ListNode fast = head, slow = head;

        // 2. runner
        /*
        fast는 2칸씩, slow 1칸씩 이동
        fast가 끝에 도달하면, slow는 링크드 리스트 중앙에 위치한다.
        fast가 2칸 이동 할 수 있을 때 까지 탐색한다.        
        */
        while(fast != null && fast.next != null) {
            fast = fast.next.next;
            slow = slow.next;

            if(fast == slow) return true;
        }

        return false;
    }
}
```

# 3. javascript
```js
const hasCycle = function(head) {
    // 1. init
    let fast = head
    let slow = head
    
    // 2. runner
    while (fast && fast.next) {
        fast = fast.next.next
        slow = slow.next
        
        if(fast == slow) return true
    }
    
    return false
};
```