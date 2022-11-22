
### 1. python
```python
from collections import defaultdict

n, q = map(int, input().split())

d = defaultdict(set)

for _ in range(q):
    c, s, e = map(int, input().split())
    if c == 1:
        d[s].add(e)
    elif c == 2:
        if e in d[s]:
            d[s].remove(e)
    else:
        res1 = True if e in d[s] else False
        res2 = True if s in d[e] else False
        print('Yes' if res1 and res2 else 'No')
```