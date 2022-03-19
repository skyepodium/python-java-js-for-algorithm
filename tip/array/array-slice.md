# 배열 자르기

# 1. python
슬라이싱을 적극 활용합니다. 슬라이싱이 제일 빠르고 효율적입니다.

```python
a = ['a', 'b', 'c', 'd']

b = list(a[:2])

print(b)
```

# 2. java
copyOfRange 을 사용합니다.
```java
class Main {
    public static void main(String[] args) {
        String[] a = {"a", "b", "c", "d"};

        String[] b = Arrays.copyOfRange(a, 0, 2);

        Arrays.stream(b).forEach(System.out::println);
    }
}
```

# 3. javascript
slice 를 사용합니다.
```js
const a = ['a', 'b', 'c', 'd']

const b = a.slice(0, 2)

console.log('b', b)
```