# 전체 문자열이 정규표현식과 맞는지 검사

# 1. Python
`re` 의 `fullmatch`를 사용합니다.
```python
import re

s = "HelloWorld"

res = re.fullmatch("[a-zA-Z]+", s)

if res:
    print(res.group()) # HelloWorld

```

# 2. Java
시작 `^` - 끝 `$` 넣어서 정규식 만들고 Pattern, Matcher 사용합니다.

```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

class Main {
    public static void main(String[] args) {
        String s = "HelloWorld";

        Pattern pattern = Pattern.compile("^[a-zA-Z]+$");
        Matcher matcher = pattern.matcher(s);
        if(matcher.find()) {
            System.out.println(matcher.group());
        }
    }
}
```

# 3. JavaScript
정규표현식의 test 메서드를 사용합니다.
```js
const s = "HelloWorld"

const r = /[a-zA-Z]+/

const res = r.test(s)

if(res) {
    console.log(r.exec(s)[0]) // HelloWorld
}
```