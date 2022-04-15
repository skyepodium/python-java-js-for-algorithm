# 1. 설명
- first, second 다음에 오는 third 단어들을 반환하세요


[문제 링크](https://leetcode.com/problems/occurrences-after-bigram/)


# 2. 코드
### 1) Python
```python
class Solution:
    def findOcurrences(self, text: str, first: str, second: str) -> List[str]:

        return re.findall(f"(?= {first} {second} (\w+))", f" {text}")
```

### 2) Java
```java
import java.util.ArrayList;
import java.util.List;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

class Solution {
    public String[] findOcurrences(String text, String first, String second) {
        Pattern pattern = Pattern.compile(String.format("(?= %s %s (\\w+))", first, second));

        List<String> res = new ArrayList<>();

        Matcher matcher = pattern.matcher(" " + text);
        while(matcher.find()) {
            res.add(matcher.group(1));
        }

        return res.toArray(new String[res.size()]);
    }
}
```

### 3) JavaScript
```js
const findOcurrences = (text, first, second) => {

    return [...` ${text}`.matchAll(new RegExp(`(?= ${first} ${second} (\\w+))`, 'g'))].map(x => x[1])
};
```