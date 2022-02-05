# 1. 설명
- 해시맵을 만드세요.


[문제 링크](https://leetcode.com/problems/design-hashmap)

해시맵을 만드는 2가지 방법
1. separate chaining(자바, C++, go)
2. open address(파이썬, 루비)


# 2. 코드
### 1) python
#### Seperate Chaining
```python
class MyHashMap:
    def __init__(self):
        self.size = 1000
        self.table = [None] * self.size

    def get_idx(self, key):
        return key % self.size

    def put(self, key: int, value: int) -> None:
        idx = self.get_idx(key)

        node = self.table[idx]
        # 1) not exist
        if not node: self.table[idx] = ListNode(key, value)

        # 2) exist
        else:
            prev = None

            while node:
                # duplicated key
                if node.key == key:
                    node.value = value
                    break
                # search
                prev, node = node, node.next
            # not found
            if not node: prev.next = ListNode(key, value)

    def get(self, key: int) -> int:
        idx = self.get_idx(key)

        node = self.table[idx]
        res = -1

        while node:
            if node.key == key:
                res = node.value
                break

            node = node.next

        return res

    def remove(self, key: int) -> None:
        idx = self.get_idx(key)

        prev, node = None, self.table[idx]

        while node:
            if node.key == key:
                if not prev:
                    self.table[idx] = node.next
                    return
                elif not node.next:
                    prev.next = None
                    return
                else:
                    prev.next = node.next
                    return

            prev, node = node, node.next

        return None


class ListNode:
    def __init__(self, key, value):
        self.key = key
        self.value = value
        self.next = None
```

### 2) java
#### Seperate Chaining
```java
class MyHashMap {

    private int size;
    private Node[] table;

    public MyHashMap() {
        this.size = 1000;
        table = new Node[1000];
    }

    public int getIdx(int key) {
        return key % this.size;
    }

    public void put(int key, int value) {
        int idx = getIdx(key);

        Node node = this.table[idx];

        if (node == null) {
            this.table[idx] = new Node(key, value);
        } else {
            Node prev = null;

            while(node != null) {
                if(node.key == key) {
                    node.value = value;
                    break;
                }

                prev = node;
                node = node.next;
            }

            if(node == null) prev.next = new Node(key, value);
        }
    }

    public int get(int key) {
        int idx = getIdx(key);
        int res = -1;
        Node node = this.table[idx];

        while(node != null) {
            if(node.key == key) {
                res = node.value;
                break;
            }

            node = node.next;
        }

        return res;
    }

    public void remove(int key) {
        int idx = getIdx(key);
        Node node = this.table[idx];
        Node prev = null;

        while(node != null) {
            if(node.key == key) {
                if(prev == null) {
                    this.table[idx] = node.next;
                } else if(node.next == null) {
                    prev.next = null;
                } else {
                    prev.next = node.next;
                }
            }

            prev = node;
            node = node.next;
        }
    }
}

class Node {
    int key;
    int value;
    Node next;

    public Node(int key, int value) {
        this.key = key;
        this.value = value;
    }
}
```# 1. 설명
- 문자열 S의 부분 문자열중 중복이 없는 경우의 최대길이를 반환하세요.


[문제 링크](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

# 2. 코드
### 1) python
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        # 1. init
        d = {}
        l = 0
        res = 0

        # 2. loop
        for r, cur in enumerate(s):
            # 1) dup check
            if cur in d:
                l = max(l, d[cur] + 1)

            # 2) insert
            d[cur] = r

            # 3) update
            res = max(res, r-l+1)

        return res
```

### 2) java
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        // 1. init
        Map<Character, Integer> m = new HashMap<>();
        int n = s.length();
        int res = 0;
        int l = 0;

        // 2. loop
        for(int r=0; r<n; r++) {
            char c = s.charAt(r);

            if(m.containsKey(c)) {
                l = Math.max(l, m.get(c) + 1);
            }

            m.put(c, r);

            res = Math.max(res, r - l + 1);
        }

        return res;
    }
}
```