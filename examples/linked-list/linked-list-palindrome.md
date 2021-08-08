# 1. 설명
- 연결 리스트의 팰린드롬 여부를 반환하세요.

연결 리스트의 길이 1 <= n <= 10만



[문제 링크](https://leetcode.com/problems/palindrome-linked-list/submissions/)

# 2. 코드
### 1) python
```python
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        result = []

        # 1. 연결 리스트를 모두 꺼내서 리스트에 넣어줍니다.
        while head:
            result.append(head.val)
            head = head.next

        # 2. 슬라이싱을 통해 팰린드롬인지 확인합니다.
        return result == result[::-1]
```

### 2) java
```java
class Solution {
    public boolean isPalindrome(ListNode head) {

        ArrayList<Integer> result = new ArrayList<>();

        // 1. 연결 리스트를 모두 꺼내서 리스트에 넣어줍니다.
        while(head != null) {
            result.add(head.val);
            head = head.next;
        }

        // 2. 투 포인터를 사용해서 팰린드롬 여부를 반환합니다.
        int l = 0;
        int r = result.size() - 1;
        while(l < r) {
            if(result.get(l) != result.get(r)) return false;
            l++;
            r--;
        }

        return true;
    }
}
```