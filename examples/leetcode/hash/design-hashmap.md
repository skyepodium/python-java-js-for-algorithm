# 1. 설명
- 해시맵을 만드세요.


[문제 링크](https://leetcode.com/problems/design-hashmap)

해시맵을 만드는 2가지 방법
1. separate chaining(자바, C++, go)
2. open address(파이썬, 루비)


# 2. 코드
## 1. Seperate Chaining
### 1) python
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
            # 해시키가 변경되었기 때문에 put 함수로 값을 넣는다.
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

## 2. open address
### 1) python
```python
class MyHashMap:
    def __init__(self):
        self.count = 0
        self.size = 10
        self.deleted_size = 0
        self.table = [None] * self.size
        self.load_factor = 0.6
        self.min_factor = 3

    def _hash_code(self, key):
        return key % self.size

    def __get_entry(self, key):
        hash_key = self._hash_code(key)
        root_idx = hash_key

        for offset in range(self.size):
            new_idx = (root_idx + offset) % self.size
            node = self.table[new_idx]
            if not node or (node.key is not None and node.hash_key == hash_key and node.key == key):
                return new_idx, node

    def resize(self):
        old_table = self.table
        self.size *= self.min_factor
        self.table = [None] * self.size
        self.count = 0
        for node in old_table:
            if node and node.key is not None: self.put(node.key, node.value)

    def put(self, key: int, value: int) -> None:
        new_idx, node = self.__get_entry(key)

        if not node: self.count += 1
        self.table[new_idx] = Node(key, self._hash_code(key), value)

        if (self.deleted_size + self.count) / self.size >= self.load_factor:
            self.resize()

    def get(self, key: int) -> int:
        new_idx, node = self.__get_entry(key)
        if not node: return -1
        else: return node.value

    def remove(self, key: int) -> None:
        new_idx, node = self.__get_entry(key)
        if node and node.key is not None:
            self.table[new_idx] = Node(None, None, None)
            self.count -= 1
            self.deleted_size += 1

class Node:
    def __init__(self, key, hash_key, value):
        self.key = key
        self.hash_key = hash_key
        self.value = value
```
### 2) java
```java
import java.util.ArrayList;
import java.util.List;
import java.util.Objects;

class MyHashMap {

    private int size;
    private int deletedCount;
    private int count;
    private Node[] table;
    private final float loadFactor = (float) 0.6;
    private final int minFator = 3;
    private Node deletedNode = new Node(-1, -1, -1);

    public MyHashMap() {
        this.size = 10;
        table = new Node[this.size];
        this.count = 0;
        this.deletedCount = 0;
    }

    public int hashCode(int key) {
        return key % this.size;
    }

    public int getEntry(int key) {
        int hashKey = this.hashCode(key);
        int rootIdx = hashKey;

        for(int i=0; i<this.size; i++) {
            int newIdx = (rootIdx + i) % this.size;
            Node node = this.table[newIdx];
            if(node == null || (!node.equals(this.deletedNode) && node.hashKey == hashKey && node.key == key)) {
                return newIdx;
            }
        }

        return 0;
    }

    public void resize() {
        Node[] oldTable = this.table;
        this.size *= this.minFator;
        this.table = new Node[this.size];
        this.count = 0;

        for(Node node: oldTable) {
            if(node != null && !node.equals(this.deletedNode)) {
                this.put(node.key, node.value);
            }
        }
    }

    public void put(int key, int value) {
        int newIdx = this.getEntry(key);
        Node node = this.table[newIdx];

        if(node == null) this.count += 1;
        this.table[newIdx] = new Node(key, this.hashCode(key), value);

        if((float)((this.deletedCount + this.count) / this.size) >= this.loadFactor) {
            this.resize();
        }
    }

    public int get(int key) {
        int newIdx = this.getEntry(key);
        Node node = this.table[newIdx];
        if(node == null) return -1;
        else return node.value;
    }

    public void remove(int key) {
        int newIdx = this.getEntry(key);
        Node node = this.table[newIdx];
        if(node != null && !node.equals(this.deletedNode)) {
            this.table[newIdx] = new Node(-1, -1, -1);
            this.count -= 1;
            this.deletedCount += 1;
        }
    }
}

class Node {
    int key;
    int hashKey;
    int value;

    public Node(int key, int hashKey, int value) {
        this.key = key;
        this.hashKey = hashKey;
        this.value = value;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof Node)) return false;
        Node node = (Node) o;
        return key == node.key && hashKey == node.hashKey && value == node.value;
    }

    @Override
    public int hashCode() {
        return Objects.hash(key, hashKey, value);
    }
}
```