# 카운터

딕셔너리와 유사하나, 개수를 측정할 때 유용하게 사용되고, 연산이 된다는 특징이 있습니다.

# 1. 생성
### 1) 문자열 기반 생성
```python
from collections import Counter

s = "rabbit"

c = Counter(s)

print(c)
# Counter({'b': 2, 'r': 1, 'a': 1, 'i': 1, 't': 1})
```

### 2) 직접 넣기
defaultdict 기반으로 구성되어있어 기본값 0이 세팅된다.
```python
from collections import Counter

c = Counter()

c['a'] += 1

print(c)
```

# 2. most_common 가장 빈도수 높은 값 찾기
```python
from collections import Counter

c = Counter("rabbit")

word, cnt = c.most_common()[0]

print(word, cnt) # b 2
```

# 3. 연산
```python
from collections import Counter

a = Counter("rabbit")

b = Counter("rainbow")

print((a - b).most_common()) # [('b', 1), ('t', 1)]
```