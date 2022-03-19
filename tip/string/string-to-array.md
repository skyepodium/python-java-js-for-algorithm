# 문자열 배열로 만들기

# 1. Python
```python
s = "Hello World"

l = list(s)

print('l', l)
```

# 2. Java
```java
class Main {
    public static void main(String[] args) {
        String s = "Hello World";

        String[] l = s.split("");
        
        for(String c: l) {
            System.out.println(c);
        }
    }
}
```

# 3. JavaScript
```js
const s = "Hello Wolrd"

const l = s.split("")

console.log('l', l)
```