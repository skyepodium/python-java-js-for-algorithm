# 문자열 뒤집기

### 1) python
슬라이싱을 사용한다. 반복문 및 다른 자료형을 사용하는것 보다 더 빠르다.
```python
s = "Hello World!!!"

s = s[::-1]
```

### 2) java
StringBuffer 클래스를 사용한다.
```java
String s = "Hello World";

StringBuffer sb = new StringBuffer(s);

s = sb.reverse().toString();
```

### 3) JavaScript
```js
let s = "Hello World"

/*
    1. 문자열을 배열로 만듭니다.
    2. reverse - 배열을 뒤집습니다.
    3. join - 배열을 문자열로 합칩니다.
*/
s = s.split("").reverse().join("")
```