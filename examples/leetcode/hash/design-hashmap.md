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
        self.load_factor = 0.6
        self.count = 0

    def resize(self):
        # 기존 요소 모두 탐색
        prev_element = self.all_element()
        # 테이블 크기 * 2
        self.size *= 2
        self.table = [None] * self.size
        self.count = 0
        for key, value in prev_element:
            self.put(key, value)

    def all_element(self):
        res = []
        for node in self.table:
            while node:
                res.append((node.key, node.value))
                node = node.next
        return res

    def hash_code(self, key):
        return key % self.size

    def put(self, key: int, value: int) -> None:
        h = self.hash_code(key)

        node = self.table[h]
        # 1) 노드가 비어있는 경우
        if not node:
            self.count += 1
            self.table[h] = ListNode(key, value)
        # 2) 노드에 값이 들어있는 경우
        else:
            prev = None
            while node:
                # 노드를 찾은 경우 - value 업데이트
                if node.key == key:
                    node.value = value
                    break
                # 다음 노드로 진행
                prev, node = node, node.next
            # 노드를 찾지 못한 경우 - 맨 뒤에 새로우 노드 추가
            if not node:
                self.count += 1
                prev.next = ListNode(key, value)

        if self.count / self.size >= self.load_factor:
            self.resize()

    def get(self, key: int) -> int:
        h = self.hash_code(key)

        node = self.table[h]
        res = -1

        while node:
            # 노드를 찾은 경우 - value 반환
            if node.key == key:
                res = node.value
                break
            # 다음 노드 탐색
            node = node.next
        return res

    def remove(self, key: int) -> None:
        h = self.hash_code(key)

        prev, node = None, self.table[h]

        while node:
            if node.key == key:
                self.count -= 1
                # 1) 제일 첫번재 노드 삭제
                if not prev:
                    self.table[h] = node.next
                    break
                # 2) 제일 마지막 노드 삭제
                elif not node.next:
                    prev.next = None
                    break
                # 3) 가운데 노드 삭제
                else:
                    prev.next = node.next
                    break
            # 다음 노드 탐색
            prev, node = node, node.next
        return


class ListNode:
    def __init__(self, key, value):
        self.key = key
        self.value = value
        self.next = None
```

### 2) java
#### Seperate Chaining
```java
import java.util.ArrayList;
import java.util.List;

class MyHashMap {

    private int size;
    private Node[] table;
    private final float loadFactor = (float) 0.6;
    private int count;

    public MyHashMap() {
        this.size = 1000;
        table = new Node[this.size];
        this.count = 0;
    }

    public void resize() {
        List<Node> prevElements = this.getAllElements();
        this.size *= 2;
        this.table = new Node[this.size];
        this.count = 0;
        prevElements.forEach(x -> this.put(x.key, x.value));
    }

    public List<Node> getAllElements() {
        List<Node> res = new ArrayList<>();
        for(Node node: this.table) {
            while(node != null) {
                res.add(new Node(node.key, node.value));
                node = node.next;
            }
        }
        return res;
    }

    public int hashCode(int key) {
        return key % this.size;
    }

    public void put(int key, int value) {
        int h = hashCode(key);

        Node node = this.table[h];

        if (node == null) {
            this.count += 1;
            this.table[h] = new Node(key, value);
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

            if(node == null) {
                this.count += 1;
                prev.next = new Node(key, value);
            }
        }
        if((float)(this.count / this.size) >= this.loadFactor) {
            this.resize();
        }
    }

    public int get(int key) {
        int h = hashCode(key);
        int res = -1;
        Node node = this.table[h];

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
        int h = hashCode(key);
        Node node = this.table[h];
        Node prev = null;

        while(node != null) {
            if(node.key == key) {
                this.count -= 1;
                if(prev == null) {
                    this.table[h] = node.next;
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
```