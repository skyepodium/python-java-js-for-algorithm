# 스택

# 1. 내용
요즘 드는 생각이 스택을 굳이 배열로 구현할 필요가 있을까?

배열 기반 구현은 언젠가는 길이의 확장일 필요하다. 그렇기 때문에 공간 확장이 필요없는 링크드 리스트가 효율적이다.

인터넷 찾아봤는데 딱히 답을 얻지 못했다.


# 2. 코드
### 링크드 리스트
### 1) Python
```python
class Node:
    def __init__(self, val):
        self.val = val
        self.next = None


class Stack:
    def __init__(self):
        self.head = None
        self.cnt = 0

    def push(self, val):
        node = Node(val)
        node.next, self.head = self.head, node
        self.cnt += 1

    def pop(self):
        if not self.head: return None

        val = self.head.val
        self.head = self.head.next
        self.cnt -= 1
        return val

    def top(self):
        return self.head.val if self.head else None

    def is_empty(self):
        return self.cnt == 0

    def size(self):
        return self.cnt
```

### 2) Java
```java
class Stack <T> {
    private Node head;
    private int cnt;

    public Stack() {
        this.head = null;
        this.cnt = 0;
    }

    public void push(T val) {
        Node node = new Node(val);
        node.next = this.head;
        this.head = node;
        cnt++;
    }

    public T pop() {
        if(this.head == null) return null;

        T val = (T) this.head.val;
        this.head = this.head.next;
        this.cnt--;

        return val;
    }

    public T top() {
        if(this.head == null) return null;

        return (T) this.head.val;
    }

    public boolean isEmpty() {
        return this.cnt == 0;
    }

    public int size() {
        return this.cnt;
    }
}
```

### 3) JavaScript
```js
class Node {
    constructor(val) {
        this.val = val
        this.next = null
    }
}

class Stack {
    constructor() {
        this.head = null
        this.cnt = 0
    }

    push(val) {
        const node = new Node(val)
        node.next = this.head
        this.head = node
        this.cnt++
    }

    pop() {
        if(!this.head) return null

        const val = this.head.val
        this.head = this.head.next
        this.cnt--

        return val
    }

    top() {
        if(!this.head) return null

        return this.head.val
    }

    isEmpty() {
        return this.cnt === 0
    }

    size() {
        return this.cnt
    }
}
```