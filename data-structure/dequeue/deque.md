# 덱

# 1. 개요
queue, deque 모두 deque 만듭니다. 큐의 경우 가장 뒤에 삽입 하는 연산을 위해 더블 링크드 리스트로 구현하는 것이 효율적입니다.

더블 링크드 리스트로 구현하면 결국 deque를 위한 삭제, 삽입 연산까지 구현하면 편합니다.

# 2. 코드
### 1) Python
```python
class Node:
    def __init__(self, val):
        self.val = val
        self.next = None
        self.prev = None


class Deque:
    def __init__(self):
        self.__head = None
        self.__tail = None
        self.__cnt = 0

    def is_empty(self):
        return self.__cnt == 0

    def size(self):
        return self.__cnt

    def __increase(self):
        self.__cnt += 1

    def __decrease(self):
        if self.__cnt > 0:
            self.__cnt -= 1

    def add_first(self, val):
        node = Node(val)

        self.__head = node
        self.__tail = node

        self.__increase()

    def add_last(self, val):
        node = Node(val)

        self.__tail.next = node
        node.prev = self.__tail
        self.__tail = self.__tail.next

        self.__increase()

    def push(self, val):
        if self.is_empty():
            self.add_first(val)
        else:
            self.add_last(val)

    def pop_left(self):
        if not self.is_empty():
            head = self.__head

            if self.__head.next:
                self.__head = self.__head.next

            self.__decrease()

            return head.val
        else:
            return None

    def pop(self):
        if not self.is_empty():
            tail = self.__tail

            if tail.prev:
                self.__tail = self.__tail.prev

            self.__decrease()

            return tail.val
        else:
            return None

    def front(self):
        return self.__head.val

    def last(self):
        return self.__tail.val
```        

### 2) Java
```java
class Deque {
    private Node head;
    private Node tail;
    private int cnt;

    public Dequeue() {
        this.head = null;
        this.tail = null;
        this.cnt = 0;
    }

    public boolean isEmpty() {
        return this.cnt == 0;
    }

    public int size() {
        return this.cnt;
    }

    public void increase() {
        this.cnt++;
    }

    public void decrease() {
        if(this.cnt > 0) this.cnt--;
    }

    public void addFirst(int val) {
        Node node = new Node(val);

        this.head = node;
        this.tail = node;

        this.increase();
    }

    public void addLast(int val) {
        Node node = new Node(val);

        this.tail.next = node;
        node.prev = this.tail;
        this.tail = this.tail.next;

        this.increase();
    }

    public void push(int val) {
        if(this.isEmpty()) {
            this.addFirst(val);
        }
        else {
            this.addLast(val);
        }
    }

    public Integer popLeft() {
        if(!this.isEmpty()) {
            Node head = this.head;

            if(this.head.next != null) {
                this.head = this.head.next;
            }

            this.decrease();

            return head.val;
        }
        else {
            return null;
        }
    }

    public Integer pop() {
        if(!this.isEmpty()) {
            Node tail = this.tail;

            if(tail.prev != null) {
                this.tail = this.tail.prev;
            }

            this.decrease();

            return tail.val;
        }
        else {
            return null;
        }
    }

    public Integer front() {
        return this.head.val;
    }

    public Integer last() {
        return this.tail.val;
    }
}
```

### 3) JavaScript
```js
class Node {
    constructor(val) {
        this.val = val
        this.next = null;
        this.prev = null;
    }
}

class Dequeue {
    constructor() {
        this.head = null
        this.tail = null
        this.cnt = 0
    }

    isEmpty() {
        return this.cnt === 0
    }

    size() {
        return this.cnt
    }

    increase() {
        this.cnt++
    }

    decrease() {
        if(this.cnt > 0) this.cnt--
    }

    addFirst(val) {
        const node = new Node(val)

        this.head = node
        this.tail = node

        this.increase()
    }

    addLast(val) {
        const node = new Node(val)

        this.tail.next = node
        node.prev = this.tail
        this.tail = this.tail.next

        this.increase()
    }

    push(val) {
        if(this.isEmpty()) {
            this.addFirst(val)
        }
        else {
            this.addLast(val)
        }
    }

    popLeft() {
        if(!this.isEmpty()) {
            const head = this.head

            if(this.head.next) {
                this.head = this.head.next
            }

            this.decrease()

            return head.val
        }
        else {
            return null
        }
    }

    pop() {
        if(!this.isEmpty()) {
            const tail = this.tail

            if(tail.prev) {
                this.tail = this.tail.prev
            }

            this.decrease()

            return tail.val
        }
        else {
            return null
        }
    }

    front() {
        return this.head.val
    }

    last() {
        return this.tail.val
    }
}
```