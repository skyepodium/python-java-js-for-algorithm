# 정렬 - 문자열 배열

# 1. Python
파이썬은 알아서 잘 해줍니다.
```python
l = ["다", "가", "나", "라", "마"]

l.sort()

print(l)
# ['가', '나', '다', '라', '마']
```

# 2. Java
`compareTo`를 사용합니다.
```java
import java.util.Arrays;

class Main {
    public static void main(String[] args) {
        String[] l = {"다", "가", "나", "라", "마"};

        Arrays.stream(l).sorted(String::compareTo)
                .forEach(System.out::println);
        // 가나다라마
    }
}
```

# 3. JavaScript
`localeCompare`을 사용합니다.

```js
const l = ["다", "가", "나", "라", "마"]

l.sort((a, b) => a.localeCompare(b))

console.log('l', l)
// l [ '가', '나', '다', '라', '마' ]
```