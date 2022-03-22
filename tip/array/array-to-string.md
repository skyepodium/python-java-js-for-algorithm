배열을 문자열로 변환

# 1. python
```python
### 1) 문자 배열 join
a = ['a', 'b', 'c', 'd']

res = " ".join(a)

print(res)

# 2. 숫자 배열은 각 원소를 모두 문자로 변경 후 join 사용
b = [1, 2, 3, 4]

r = " ".join(map(str, b))

print(r)
```

# 2. java
```java
class Main {
    public static void main(String[] args) {
        String[] a = {"a", "b", "c", "d"};
        String res = String.join(" ", a);

        System.out.println(res);
    }
}
```

# 3. JavaScript
```js
const a = ['a', 'b', 'c', 'd']

const res = a.join("")

console.log('res', res)
```