# 파이썬 zip을 자바스크립트 제너레이터로 구현

파이썬의 zip 함수가 필요한 경우가 있습니다. 이 경우 제너레이터를 통해 구현합니다. 

### 1. python
```python
a = [1, 2, 3, 4, 5, 6, 7]
b = ['a', 'b', 'c', 'd', 'e']

for x, y in zip(a, b):
    print(x, y)
"""
1 a
2 b
3 c
4 d
5 e
"""
```

### 2. java
```java
const a = [1, 2, 3, 4, 5]
const b = ['a', 'b', 'c', 'd', 'e']

function* zip(a, b) {
    const n = Math.min(a.length, b.length)

    for (let i = 0; i < n; i++) yield [a[i], b[i]]
}

for(const q of zip(a, b)) {
    console.log(q)
}

[...zip(a, b)].forEach(x => console.log(x))
```