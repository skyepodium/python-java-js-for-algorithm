
# 문자열을 특정 단어 기준으로 분리해서 리스트로 만들기

split 함수
- 파이썬 - split() 함수는 문자열로 분리한다.
- 자바 - split() 함수는 정규표현식을 기준으로 분리한다.
- 자바스크립트 - split() 함수는 정규식, 문자열 기준으로 분리한다. 

단어 사이의 공백이 1개 이상인 경우 정규표현식을 사용한다.
```js
// 1) 띄어쓰기 -> 공백, 2) + -> 1개 이상
" +"
```
파이썬은 split()함수에 아무것도 안넣으면 1개 이상의 공백으로 분리한다.

# 1. Python
문자열의 split 함수 이용
```python
a = "a b  c   d    e"

res = a.split()
print(res)
# [a, b, c, d, e]
```
정규표현식을 이용한 분리
```python
import re

a = "a b  c   d    e"

res = re.split(" +", a)
print(res)
# [a, b, c, d, e]
```

# 2. Java
자바의 split함수는 정규표현식을 사용한다.
```java
import java.util.Arrays;

class Main {
    public static void main(String[] args) {
        String a = "a b  c   d    e";

        String[] p = a.split(" +");

        // [a, b, c, d, e]
        Arrays.stream(p).forEach(System.out::println);
    }
}
```

# 3. JavaScript
정규식도 적용가능하다.
```js
const a = "a b  c   d    e"

const res = a.split(/[ ]+/)

console.log('res', res)
```