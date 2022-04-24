# 정규표현식으로 특정 문자열 모두 검색

# 1. Python
`re` 의 `findall` 메서드를 사용합니다.

```python
import re

s = " abcd ef gh i jklm "

res = re.findall("[a-z]+", s)

print('res', res) # res ['abcd', 'ef', 'gh', 'i', 'jklm']
```


# 2. Java
pattern과 matcher를 사용합니다.

```java
import java.util.ArrayList;
import java.util.List;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

class Main {
    public static void main(String[] args) {

        Pattern pattern = Pattern.compile("[a-z]+");
        String s = " abcd ef gh i jklm ";
        List<String> res = new ArrayList<>();

        Matcher matcher = pattern.matcher(s);
        while(matcher.find()) {
            res.add(matcher.group());
        }

        res.stream().forEach(x -> System.out.print(x + " ")); // abcd ef gh i jklm
    }
}
```

# 3. JavaScript
### 1) matchall, 구조분해
```js
const s = " abcd ef gh i jklm "

const re = /[a-z]+/g

const res = [...s.matchAll(new RegExp(re))].map(x => x[0])

console.log('res', res) // [ 'abcd', 'ef', 'gh', 'i', 'jklm' ]
```

### 2) exec
정규표현식의 exec 메서드를 사용합니다.

정규표현식 생성할때 글로벌 옵션 `g` 넣는것 잊지 맙시다.
```js
const s = " abcd ef gh i jklm "

const re = /[a-z]+/g
const res = []

let match = re.exec(s)
while(match) {
    res.push(match[0])
    match = re.exec(s)
}

console.log('res', res) // [ 'abcd', 'ef', 'gh', 'i', 'jklm' ]

```