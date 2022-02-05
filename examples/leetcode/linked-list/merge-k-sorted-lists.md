# 1. 설명
- 정렬된 링크드 리스트를 병합 후 반환하세요.


[문제 링크](https://leetcode.com/problems/merge-k-sorted-lists/)

# 비고
Hard 문제가 되려면 n이 더 커야할듯

# 2. 코드
### 1) python
```python
class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        # 1. init
        head = node = None
        nums = []

        # 2. loop
        for c in lists:
            while c:
                nums.append(c.val)
                c = c.next

        # 3. sort
        nums.sort()

        # 4. loop
        for n in nums:
            if node:
                node.next = ListNode(n, None)
                node = node.next
            else:
                head = node = ListNode(n, None)

        return head
```

### 2) java
```java
class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        // 1. init
        ListNode head = null, node = null;
        List<Integer> l = new ArrayList<>();

        // 2. loop
        for(ListNode c: lists) {
            while(c != null) {
                l.add(c.val);
                c = c.next;
            }
        }

        // 3. sort
        l.sort(Comparator.comparingInt(a -> a));

        // 4. loop
        for(Integer n: l) {
            if(node == null) {
                head = node = new ListNode(n, null);
            }
            else {
                node.next = new ListNode(n, null);
                node = node.next;
            }
        }

        return head;
    }
}
```