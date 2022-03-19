# 문자열 정렬
# 1. python

```python
a = "edcba"

# sorted는 리스트를 반환한다.
a = "".join(sorted(a))
```

# 2. java
```java
String a = "edcba";

// 1. 문자열을 char array로 변경
char[] charArray = a.toCharArray();

// 2. Arrays sort를 사용해서 배열 정렬, 반환값 없음
Arrays.sort(charArray);

// 3. char array를 String 클래스로 생성
a = new String(charArray);
```

# 3. JavaScript
```js
let a = "edcba"

a = a.split("").sort().join("")

console.log('a', a)
```