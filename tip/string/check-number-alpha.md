# 숫자, 알파벳 여부 판별

간단한 내용이고, 사실 파이썬의 `isalpha`, `isdigit`을 소개하기 위한 내용입니다.

다른 언어의 경우 직접 구현하면 됩니다.

### 참고
정규표현식에서 `\w`는 영문자, 숫자, 밑줄이 포함됩니다. 영문자만 포함하지는 않습니다.

# 1. Python
```python
a = "a"

print(a.isalpha())
# True

b = "0"

print(b.isdigit())
# True
```

# 2. Java
```java
class Main {
    public static void main(String[] args) {
        String a = "a";
        System.out.println(a.matches("[a-zA-Z]"));
        // true

        String b = "0";
        System.out.println(b.matches("\\d"));
        // true
    }
}
```

# 3. JavaScript
```js
const a = "a"

console.log(/[a-zA-Z]/.test(a))
// true

const b = "0"
console.log(/\d/.test(b))
// true
```

