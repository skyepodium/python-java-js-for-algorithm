# 1. 설명
- 규칙에 맞는 단어의 개수를 구하세요

[문제 링크](https://leetcode.com/problems/number-of-valid-words-in-a-sentence/)

# 2. 코드
### 1) Python
```python
class Solution:
    def countValidWords(self, sentence: str) -> int:
        # 1. init
        res = 0

        # 2. loop
        for r in re.split(" +", sentence):
            if re.fullmatch("[a-z]+", r) and r.lower() == r:
                res += 1
            elif re.fullmatch("[a-z]+-[a-z]+[\\.!, ]*", r):
                res += 1
            elif re.fullmatch("[a-z]*[\\.!, ]", r):
                res += 1

        return res
```

### 2) Java
```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

class Solution {
    public int countValidWords(String sentence) {
        // 1. init
        int res = 0;

        // 2. loop
        for(String r: sentence.split(" +")) {
            // 1) lower
            Pattern pattern = Pattern.compile("^[a-z]+$");
            Matcher matcher = pattern.matcher(r);
            if(matcher.find()) res++;

            // 2) hypen
            pattern = Pattern.compile("^[a-z]+-[a-z]+[\\.!, ]*$");
            matcher = pattern.matcher(r);
            if(matcher.find()) if(r.toLowerCase().equals(r)) res++;

            // 3) punctuation
            pattern = Pattern.compile("^[a-z]*[\\.!, ]$");
            matcher = pattern.matcher(r);
            if(matcher.find()) if(r.toLowerCase().equals(r)) res++;

        }

        return res;
    }
}
```

### 3) JavaScript
```js
const countValidWords = (sentence) => {
    // 1. init
    let res = 0

    // 2. loop
    for(const r of sentence.split(/ +/)) {
        // 1) lower
        if(new RegExp(/^[a-z]+$/g).test(r)) res++
        else if(new RegExp(/^[a-z]+-[a-z]+[\\.!, ]*$/g).test(r)) res++
        else if(new RegExp(/^[a-z]*[\\.!, ]$/g).test(r)) res++
    }

    return res
};
```