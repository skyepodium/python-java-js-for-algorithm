# 1. 설명
- 최소값 스택을 구현하세요


[문제 링크](https://leetcode.com/problems/min-stack/)


# 2. 코드
### 1) python
```python
class Node:
    def __init__(self, val, min_val):
        self.val = val
        self.next = None
        self.min_val = min_val


class MinStack:

    def __init__(self):
        self.head = None

    def push(self, val: int) -> None:
        node = Node(val, min(val, self.head.min_val) if self.head else val)
        node.next = self.head
        self.head = node

    def pop(self) -> None:
        self.head = self.head.next

    def top(self) -> int:
        return self.head.val

    def getMin(self) -> int:
        return self.head.min_val
```

### 2) java
```java
class MinStack {
    private Node head;

    public MinStack() {
        this.head = null;
    }

    public void push(int val) {
        Node node = new Node(val, this.head != null ? Math.min(this.head.minVal, val) : val);
        node.next = this.head;
        this.head = node;
    }

    public void pop() {
        this.head = this.head.next;
    }

    public int top() {
        return this.head.val;
    }

    public int getMin() {
        return this.head.minVal;
    }
}

class Node {
    public int val;
    public int minVal;
    public Node next;

    public Node(int val, int minVal) {
        this.val = val;
        this.minVal = minVal;
    }
}
```

### 3) JavaScript
```js
class Node {
    constructor(val, minVal) {
        this.val = val
        this.next = null
        this.minVal = minVal
    }
}

const MinStack = function() {
    this.head = null
};

MinStack.prototype.push = function(val) {
    const minVal = this.head ? Math.min(val, this.head.minVal) : val
    const node = new Node(val, minVal)
    node.next = this.head
    this.head = node
};


MinStack.prototype.pop = function() {
    this.head = this.head.next
};


MinStack.prototype.top = function() {
    return this.head.val
};


MinStack.prototype.getMin = function() {
    return this.head.minVal
};
```