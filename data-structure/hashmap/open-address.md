# 해시맵

# 참고
해시맵을 만드는 방법은 크게 2가지입니다. 
1. Separate chaining - 배열 + 링크드리스트
2. Open Address - 배열, 삭제된 자리에는 더 이상 저장하지 않음, 리사이징할때 초기화됨

파이썬은 Open Address, 자바는 Separate chaining으로 구성되어있습니다. 

2개 모두 구현해봅시다.

[leetcode - design-hashmap](https://leetcode.com/problems/design-hashmap/) - Open Address

# 1.  python
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

# 2. java
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