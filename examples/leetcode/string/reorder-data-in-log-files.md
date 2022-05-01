# 1. 설명
- 각 문자열의 첫번째는 identifier이다.

- letter-logs - 영소문자로 구성되어있다.
- digit-logs - 숫자로 구성되어 있다.

- letter-logs는 digit-logs 이후에 온다.
- letter-logs는 사전순으로 정렬한다. 만약 같으면 identifier의 사전순으로 정렬한다.
- digit-logs는 현 순서를 유지한다.


[문제 링크](https://leetcode.com/problems/reorder-data-in-log-files/)


# 2. 코드
### 1) python

정렬 조건만으로 분리
- comparator와 동적 조건을 사용할 수 있기 때문에 적용가능
```python
class Solution:
    def reorderLogFiles(self, logs: List[str]) -> List[str]:

        def get_key(s):
            i, c = s.split(" ", maxsplit=1)
            return (0, c, i) if c[0].isalpha() else (1, )

        return sorted(logs, key=get_key)
```

```python
class Solution:
    def reorderLogFiles(self, logs: list[str]) -> list[str]:
        
        letters = []
        digits = []
        
        for log in logs:
            # 1. identifier를 제외한 content가 숫자이면
            if log.split(" ")[1].isdigit():
                digits.append(log)
            # 2. content가 문자이면
            else:
                letters.append(log)
                
        # 3. letters를 사전순으로 정렬한다. 만약 같으면 identifier 사전순으로 정렬한다.      
        letters.sort(key=lambda x: (x.split(" ")[1:], x.split(" ")[0]))                
        # 4. letters 이후에 digits가 온다.
        return letters + digits
        
```

### 2) java
```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public String[] reorderLogFiles(String[] logs) {
        // 1. init
        List<String> letters = new ArrayList<>();
        List<String> digits = new ArrayList<>();

        // 2. loop
        for(String l: logs) {
            String[] ls = splitByTwo(l);

            if(isNumber(ls[1].charAt(0))) digits.add(l);
            else letters.add(l);
        }

        // 3. sort
        letters.sort((a, b) -> {
            String[] ar = splitByTwo(a);
            String[] br = splitByTwo(b);

            return ar[1].equals(br[1]) ? ar[0].compareTo(br[0]) : ar[1].compareTo(br[1]);
        });

        // 4. addAll
        letters.addAll(digits);

        return letters.toArray(new String[0]);
    }

    public String[] splitByTwo(String s) {
        return s.split(" ", 2);
    }

    public boolean isNumber(char c) {
        return (int)c >= (int)'0' && (int)c <= (int)'9';
    }
}
```

### 3) JavaScript
```js
const reorderLogFiles = (logs) => {
    // 1. splitByTwo
    const splitByTwo = (s) => {
        const idx = s.indexOf(" ")
        return [s.slice(0, idx), s.slice(idx+1)]
    }

    // 2. isNumber
    const isNumber = (c) => {
        return /\d/.test(c)
    }

    // 3. init
    const letters = [], digits = []

    // 4. sort
    logs.forEach(s => {
        const [, contents] = splitByTwo(s)

        if(isNumber(contents[0])) digits.push(s)
        else letters.push(s)
    })

    letters.sort((a, b) => {
        const [ai, ac] = splitByTwo(a)
        const [bi, bc] = splitByTwo(b)

        return ac === bc ? ai.localeCompare(bi) : ac.localeCompare(bc)
    })

    return letters.concat(digits)
};
```