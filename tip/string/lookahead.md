# 문자열에서 중첩된 부분까지 정규표현식으로 찾기 - 전방탐색

`we will` 다음에 오는 첫번째 단어를 찾으려고 합니다.

다만, 정규표현식은 기본적으로 찾은 문자열을 `소비` 하기 때문에

찾은 내용에 대해서 중첩으로 검사하는 것이 불가능합니다.

['we', 'rock'] 을 찾는 것이 목적이지만, ['we'] 만 검색됩니다.

```python
import re

s = "we will we will rock you"

res = re.findall("we will (\w+)", s)

print('res', res) # ['we']
```

이러한 경우 전방탐색을 사용할 수 있습니다.

전방탐색은 해당 문자열을 소비하지 않고 검색 결과에서 제외할 수 있습니다.

# 1. Python
```py
import re

s = "we will we will rock you"

res = re.findall(f"(?=we will (\w+))", s)

print('res', res) # ['we', 'rock']
```

# 2. Java
```java
import java.util.ArrayList;
import java.util.List;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

class Main {
    public static void main(String[] args) {

        String s = "we will we will rock you";

        Pattern pattern = Pattern.compile("(?=we will (\\w+))");

        List<String> res = new ArrayList<>();

        Matcher matcher = pattern.matcher(s);
        while(matcher.find()) {
            res.add(matcher.group(1));
        }

        res.forEach(System.out::println);
        /*
            we
            rock
         */
    }
}
```

# 3. JavaScript
```js
const s = "we will we will rock you"

const res = [...s.matchAll(new RegExp('(?=we will (\\w+))', 'g'))].map(x => x[1])

console.log('res', res) // [ 'we', 'rock' ]

```