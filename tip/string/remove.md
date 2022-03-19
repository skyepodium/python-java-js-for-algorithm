# 특정 문자열 제거

# 1. Python
```python
# 영문자, 숫자, 공백에 포함되지 않는 문자 제거
import re

s = "Hello World!!! 2021~~ 찡긋"

s = re.sub("[^a-zA-z0-9 ]", '', s)

print(s) # Hello World 2021 
```

# 2. Java
```java
class Main {
    public static void main(String[] args) {
        // 영문자, 숫자, 공백에 포함되지 않는 문자 제거
        String s = "Hello World!!! 2021~~ 찡긋";

        s = s.replaceAll("[^a-zA-z0-9 ]", "");

        System.out.println(s); // Hello World 2021 
    }
}
```

# 3. JavaScript
참고로 `replaceAll`은 node.js 환경에서 제대로 작동하지 않는다.
```js
let s = "Hello World!!! 2021~~ 찡긋"

s = s.replaceAll(/[^a-zA-Z0-9 ]/g, '')

console.log(s) // Hello World 2021 
```