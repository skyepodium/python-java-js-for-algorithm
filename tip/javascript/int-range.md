# 정수형 범위 - 예시) 1) shift 연산 vs Math.pow, 2) not not vs Math.trunc

# 1. 내용
자바스크립트의 일부 함수는 `정수형 범위(-2147483648 ~  2147483647)`만 지원합니다.

# 2. 예시
### 1) shift 연산 vs Math.pow
정수형 범위라는 확인이 있으면 간단하게 shift 연산 사용하고

정확성이 필요하다면, `Math.pow` 사용합시다.
```js
const n = 31

// 1. shift 연산 - 정수 범위
a = Math.pow(2, n)
b = 1 << n // shift 연산의 경우 정수 범위 넘어서 음수가 됩니다.

console.log(a, b, a === b)
// 2147483648 -2147483648 false

// 2. shift 연산 - BigInt
a = Math.pow(2, n)
b = BigInt(1) << BigInt(n)
// BigInt 사용하면 터지지는 않지만 BigInt 자료형이 됩니다.

console.log(a, b, a === b)
// 2147483648 2147483648n false
```

### 2) not not vs Math.trunc
`~~ not not` 에는 `BigInt`도 적용되지 않습니다.

정확성이 필요하면 `Math.trunc` 사용합시다.

```js
const n = 2147483648

const a = ~~(n)
console.log('a', a) // -2147483648
console.log('a big', ~~(BigInt(a))) // -2147483648n

const b = Math.trunc(n)
console.log('b', b) // 2147483648

console.log(a === b) // false
```