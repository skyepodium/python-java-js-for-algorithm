# 파이썬 zip을 자바스크립트 제너레이터로 구현

파이썬의 zip 함수가 필요한 경우가 있습니다. 이 경우 제너레이터를 통해 구현합니다. 

### 1. Python
### 1) zip
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

### 2) zip_longest 
```python
from itertools import zip_longest

a = [1, 2, 3, 4, 5, 6, 7]
b = ['a', 'b', 'c', 'd', 'e']

for x, y in zip_longest(a, b, fillvalue=""):
    print(x, y)

"""
1 a
2 b
3 c
4 d
5 e
6 
7 
"""
```

### 2. JavaScript
### 1) zip
```js
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

/*
[ 1, 'a' ]
[ 2, 'b' ]
[ 3, 'c' ]
[ 4, 'd' ]
[ 5, 'e' ]
[ 1, 'a' ]
[ 2, 'b' ]
[ 3, 'c' ]
[ 4, 'd' ]
[ 5, 'e' ]
*/
```

### 2) zipLongest
```js
function* zipLongest(a, b, fillValue) {
    const n = Math.max(a.length, b.length)

    for (let i = 0; i < n; i++) {
        const aVal = i < a.length ? a[i] : fillValue
        const bVal = i < b.length ? b[i] : fillValue
        yield [aVal, bVal]
    }
}

const a = [1, 2, 3, 4, 5]
const b = ['a', 'b', 'c', 'd', 'e', 'f', 'g']

for(const [x, y] of zipLongest(a, b, "")) {
    console.log(x, y)
}
/*
1 a
2 b
3 c
4 d
5 e
 f
 g
*/
```