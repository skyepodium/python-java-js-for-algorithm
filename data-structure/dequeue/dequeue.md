# 덱

# 1. 개요
queue, deueue 모두 dequeue로 만듭니다. 큐의 경우 가장 뒤에 삽입 하는 연산을 위해 더블 링크드 리스트로 구현하는 것이 효율적이고

더블 링크드 리스트로 구현하면 결국 덱이 됩니다. 

# 2. 코드
### 1) Python
```python
class Node:
    def __init__(self, val):
        self.val = val
        self.next = None
        self.prev = None


class Dequeue:
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
