# 특정 문자열 제거

와일드 카드 .(마침표)는 집합(대괄호 [])안에 있으면 이스케이프 문자열을 사용하지 않아도됩니다.

# 1. Python
```python
import re

s = "ab.cd.e"

a = re.sub("[.]", "", s)
print('a', a) # a abcde

b = re.sub("\\.", "", s)
print('b', b) # b abcde
```

# 2. Java

```java
class Main {
    public static void main(String[] args) {
        String s = "ab.cd.e";

        String a = s.replaceAll("[.]", "");
        System.out.println("a " + a); // a abcde

        String b = s.replaceAll("\\.", "");
        System.out.println("b " + b); // b abcde
    }
}
```

# 3. JavaScript
이스케이프 문자 1개만 사용해야합니다.
```js
const s = "ab.cd.e"

const a = s.replace(/[.]/g, "")
console.log('a', a) // a abcde

const b = s.replace(/\./g, "")
console.log('b', b) // b abcde
```