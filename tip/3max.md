원소 3개의 최대값, 최소값을 구하는 경우 있습니다.

if문 여러개 사용하지 말고, max 2개를 중첩해서 사용합니다.

# 1. python
파이썬은 그럴 필요없습니다. max 내장 함수 사용합니다.
```python
a, b, c = 0, 1, 2

res = max(a, b, c)

print('res', res)
```

# 2. java
```java
class Main {
    public static void main(String[] args) {
        
        int a = 0, b = 1, c = 3;
        
        int res = Math.max(a, Math.max(b, c));

        System.out.println("res " + res);
    }
}
```

# 3. javascript
JS도 Math.max 내장 함수 잘 사용하면 됩니다.
```js
const a = 0
const b = 1
const c = 3

const res = Math.max(a, b, c)

console.log('res', res)
```