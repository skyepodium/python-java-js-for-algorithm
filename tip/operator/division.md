# 정수 나눗셈, 몫 구하기

음수 나눗셈 까지 고려해야한다면

# 1. Python
- `//` - 음수 나눗셈 X
- `math.trunc` - 음수 나눗셈 O

`//`만 사용해도 큰 문제가 없었는데, 아마도 알고리즘에서는 음수 나눗셈 할일이 거의 없기 때문이듯

머신러닝 할때는 음수 나눗셈 많이 나옴
```python
a = 10
b = 3

print(a//b) # 3

import math

res = math.trunc(-10/3)

print(res) # -3
```

# 2. Java
`/` 연산자를 사용합니다.
```java
class Main {
    public static void main(String[] args) {

        System.out.println(a/b);
        System.out.println(-10/3);
    }
}
```

# 3. JavaScript
`Math.trunc` 연산자를 사용합니다.

정수형 범위 이내라고 확신한다면 `not not ~~` 사용가능합니다.

- ~~(not not) - bitwise not 중첩 - 음수 나눗셈 O
- Math.trunc - 버림 - 음수 나눗셈 O
- Math.floor - 내림 - 음수 나눗셈 X
```js
const a = -10
const b = 3

console.log('Math.floor', Math.floor(a/b)) // Math.floor -4
console.log('Math.trunc', Math.trunc(a/b)) // Math.trunc -3
console.log('not not', ~~(a/b)) // not not -3
```

`not not`의 최대범위는 정수 범위입니다. [콜라츠 추측
](https://programmers.co.kr/learn/courses/30/lessons/12943?language=javascript) 문제는 `not not` 사용하면 중간에 터집니다.
```js
// 1. 정수 범위
const n = 2147483647
console.log('res', ~~n) // 2147483647

// 2. 정수 범위 초과
console.log('res', ~~(n+1)) // -2147483648

// 3. 연산결과가 정수형 범위 초가
console.log('res', ~~((n * 2 + 2) / 2)) // -2147483648
```