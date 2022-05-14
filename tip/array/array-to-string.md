배열을 문자열로 변환

# 1. Python
파이썬의 경우 int는 str로 변경해서 join걸어야 합니다.

가끔씩 잊어서 에러가 발생합니다.
```python
### 1) 문자 배열 join
a = ['a', 'b', 'c', 'd']

res = "".join(a) # abcd

print(res)

# 2. 숫자 배열은 각 원소를 모두 문자로 변경 후 join 사용
b = [1, 2, 3, 4]

r = "".join(map(str, b)) # 1234

print(r)
```

# 2. Java
자바도 정수는 문자열로 변경해서 사용합니다.

```java
import java.util.Arrays;
import java.util.stream.Collectors;

class Main {
    public static void main(String[] args) {

        String[] a = {"a", "b", "c", "d"};
        String res = String.join("", a);

        System.out.println(res); // abcd

        int[] b = {1, 2, 3, 4};
        String r = Arrays.stream(b).mapToObj(Integer::toString).collect(Collectors.joining(""));

        System.out.println(r); // 1234
    }
}
```

# 3. JavaScript
자바스크립트의 경우 number는 string으로 자동 파싱됩니다.

```js
const a = ['a', 'b', 'c', 'd']

const res = a.join("")

console.log('res', res) // abcd

const b = [1, 2, 3, 4]

const r = b.join("")

console.log('r', r) // 1234
```