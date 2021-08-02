# 요즘은...
요즘은 코딩테스트를 보면, 언어에 제한을 두는 경우가 있습니다.

- Front - JavaScript
- Machine Learning - python
- Server - Java, Python

뭔가,Server 엔지니어는 2개의 언어를 사용하다보면, 조금 헷갈릴 때가 있어서 

그냥 정리해보려구

# 문법
python, java를 같이 쓰다보니 햇갈리기 시작했다.

정리해보자

# 1. 정규 표현식
### 1) python

```python
# 영문자, 숫자에 포함되지 않는 문자 제거
import re

s = "Hello World!!! 2021~~ 찡긋"

s = re.sub("[^a-zA-z0-9]", '', s)
```

### 2) java
```java
// 영문자, 숫자에 포함되지 않는 문자 제거
String s = "Hello World!!! 2021~~ 찡긋";

s = s.replaceAll("[^a-zA-z0-9]", "");
```

# 2. 문자열 뒤집기
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

# 3. 리스트 뒤집기
### 1) python
- 슬라이싱 - 값 반환, 공간복잡도 O(n)
- reverse() - 내부 변경, 공간복잡도 O(1)
```python
s = [1, 2, 3]

# 슬라이싱
s[::-1]

# 내부 변경
s.reverse()
```
### 2) java
투 포인터, 스왑
```java
int[] s = {1, 2, 3};
// 투포인터
int l = 0;
int r = s.length - 1;

while(l < r) {
    // 스왑
    int temp = s[l];
    s[l] = s[r];
    s[r] = temp;
    l++;
    r--;
}
```

# 6. 대문자, 소문자로 변경
### 1) python
```python
s = "Hello World"

# 소문자
s.lower()

# 영문자
s.upper()
```

### 2) java
```java
String s = "Hello World";

// 소문자
s.toLowerCase();

// 대문자
s.toUpperCase();
```