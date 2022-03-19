# defaultdict

# 1. 기본값
파이썬 딕셔너리를 defaultdict, 중괄호({}) 로 생성했을 때 가장 큰 차이는 기본값이다.

- defaultdict은 -  key가 없는데 넣는 경우 기본값을 세팅해준다.

- {} 중괄호 딕셔너리 - key가 없는 경우 에러 발생 
```python
from collections import defaultdict

d = defaultdict(int)
d['a'] += 1

print(d)

q = {}
# q['a'] += 1 # 에러
```

# 2. 자료형
정수형 이외에도 모든 자료형을 넣을 수 있다.
```python
from collections import defaultdict

d = defaultdict(list)
d['a'].append(1)

print(d)

class Node:
    def __init__(self, val):
        self.val = val
        self.next = None

    def __repr__(self):
        return f"{self.val} {self.next}"

n = defaultdict(Node)
n['a'] = Node(3)
print(n['a'])
```