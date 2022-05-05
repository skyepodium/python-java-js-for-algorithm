# 1. 설명
- 큐의 FIFO 연산만 가지고 스택을 구현하세요.



[문제 링크](https://leetcode.com/problems/implement-stack-using-queues/)

# 2. 코드
### 1) python
```python
class MyStack:

    def __init__(self):
        self.q = collections.deque()

    def push(self, x: int) -> None:
        self.q.append(x)
        
        for _ in range(len(self.q) - 1):
            self.q.append(self.q.popleft())
        

    def pop(self) -> int:
        return self.q.popleft()
        

    def top(self) -> int:
        return self.q[0]
        

    def empty(self) -> bool:
        return len(self.q) == 0
```

### 2) java
```java
class MyStack {

    Queue<Integer> q;

    public MyStack() {
        this.q = new LinkedList<>();
    }

    public void push(int x) {
        this.q.add(x);
        int size = q.size();
        for(int i=0; i<size-1; i++) {
            this.q.add(this.q.poll());
        }
    }

    public int pop() {
        return this.q.poll();
    }

    public int top() {
        return this.q.peek();
    }

    public boolean empty() {
        return this.q.isEmpty();
    }
}
```

### 3) JavaScript
```js
class MyStack {
    constructor() {
        this.q = []
    }

    push(x) {
        this.q.push(x)
        const n = this.q.length
        for(let i=0; i<n-1; i++) this.q.push(this.q.shift())
    }

    pop() {
        return this.q.shift()
    }

    top() {
        return this.q[0]
    }

    empty() {
        return this.q.length === 0
    }
}
```

### 4) TypeScript
```ts
class MyStack {
    q: number[]
    constructor() {
        this.q = []
    }

    push(x:number):void {
        this.q.push(x)
        const n:number = this.q.length
        for(let i=0; i<n-1; i++) this.q.push(this.q.shift()!)
    }

    pop():number {
        return this.q.shift()!
    }

    top():number {
        return this.q[0]!
    }

    empty():boolean {
        return this.q.length === 0
    }
}
```