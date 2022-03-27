# 빌트인 trim - 공백 제거

# 1. Python
`strip`을 사용합니다.
```python
s = "  abcd ef g "

print(s.strip()) # abcd ef g
```

# 2. Java
```java
class Main{
    public static void main(String[] args) {
        String s = "  abcd ef g ";

        System.out.println(s.trim()); // abcd ef g
    }
}
```

# 3. JavaScript
```js
const s = "  abcd ef g "

console.log(s.trim()) // abcd ef g
```