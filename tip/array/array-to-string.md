배열을 문자열로 변환

# 1. python
```python
a = ['a', 'b', 'c', 'd']

res = " ".join(a)

print(res)
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