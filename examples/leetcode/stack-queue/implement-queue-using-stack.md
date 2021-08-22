# 1. 설명
- 스택의 LIFO 연산만을 가지고 큐를 구현하세요.



[문제 링크](https://leetcode.com/problems/implement-queue-using-stacks/)

# 2. 코드
### 1) python
```python
class MyQueue:

    def __init__(self):
        self.left = []
        self.right = []

    def push(self, x: int) -> None:
        self.right.append(x)

    def pop(self) -> int:
        self.peek()
        return self.left.pop()

    def peek(self) -> int:
        if not self.left:
            while self.right:
                self.left.append(self.right.pop())
        return self.left[-1]

    def empty(self) -> bool:
        return len(self.left) == 0 and len(self.right) == 0
```

### 2) java
```java
import java.util.Stack;

class MyQueue {

    Stack<Integer> left, right;

    public MyQueue() {
        left = new Stack<>();
        right = new Stack<>();
    }

    public void push(int x) {
        this.right.add(x);
    }

    public int pop() {
        this.peek();
        return left.pop();
    }

    public int peek() {
        if(left.empty()){
            while(!right.empty()) {
                left.add(right.pop());
            }
        }

        return left.peek();
    }

    public boolean empty() {
        return this.left.empty() && this.right.empty();
    }
}
```