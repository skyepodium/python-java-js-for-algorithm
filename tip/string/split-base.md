
# 문자열을 특정 단어 기준으로 분리해서 리스트로 만들기

split 함수
- 파이썬 - split() 함수는 문자열로 분리한다.
- 자바 - split() 함수는 정규표현식을 기준으로 분리한다.

단어 사이의 공백이 1개 이상인 경우 정규표현식을 사용한다.
```js
// 1) 띄어쓰기 -> 공백, 2) + -> 1개 이상
" +"
```
파이썬은 split()함수에 아무것도 안넣으면 1개 이상의 공백으로 분리한다.

### 1) python
문자열의 split 함수 이용
```python
a = "a b  c   d    e"

a.split()
# [a, b, c, d, e]
```
정규표현식을 이용한 분리
```python
import re

a = "a b  c   d    e"

re.split(" +", a)
# [a, b, c, d, e]
```

### 2) java
자바의 split함수는 정규표현식을 사용한다.
```java
String a = "a b  c   d    e";

String[] p = a.split(" +");

// [a, b, c, d, e]
```