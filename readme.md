# 요즘은...
요즘은 코딩테스트를 보면, 언어에 제한을 두는 경우가 있습니다.

- Front - JavaScript
- Machine Learning - python
- Server - Java, Python

뭔가,Server 엔지니어는 2개의 언어를 사용하다보면, 조금 헷갈릴 때가 있어서 

그냥 정리해보려구

# 문제풀이
[리트코드](https://github.com/skyepodium/algorithm-for-python-java/tree/master/examples/leetcode)
[프로그래머스](https://github.com/skyepodium/algorithm-for-python-java/tree/master/examples/programmers)

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

# 3. 배열 뒤집기
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

# 4. 문자열을 특정 단어 기준으로 분리해서 리스트로 만들기
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

# 5. 문자열 정렬
### 1) python

```python
a = "edcba"

# sorted는 리스트를 반환한다.
a = "".join(sorted(a))
```

### 2) java
```java
String a = "edcba";

// 1. 문자열을 char array로 변경
char[] charArray = a.toCharArray();

// 2. Arrays sort를 사용해서 배열 정렬, 반환값 없음
Arrays.sort(charArray);

// 3. char array를 String 클래스로 생성
a = new String(charArray);
```

# 6. 문자열이 숫자인지 판별
### 1) python
```python
s = "0123456789"

# isdigit, isnumeric의 차이는
# 3², ½와 같은 것을 판별하는데 있다.
# 알고리즘에서는 만날일이 거의 없기 때문에 패스하자

s.isdigit()

s.isnumeric()
```
### 2) java
Character 클래스의 isDigit 메서드를 사용한다.

Integer.pareseInt 등의 메소드를 try, catch와 함께 사용할 수도 있지만 다음과 같은 이슈가 있다.
- 0부터 시작하는 경우
- 숫자 자료형 범위를 넘어가는 경우
```java
class Main {
    public static void main(String[] args) {

        String s = "0123456789";

        isDigit(s);
    }

    public static Boolean isDigit(String s) {
        int size = s.length();
        for(int i=0; i<size; i++) {
            if(!Character.isDigit(s.charAt(i))) return false;
        }
        return true;
    }
}
```


# 7. 대문자, 소문자로 변경
### 1) python
```python
s = "Hello World"

# 소문자
s = s.lower()

# 영문자
s = s.upper()
```

### 2) java
```java
String s = "Hello World";

// 소문자
s = s.toLowerCase();

// 대문자
s = s.toUpperCase();
```

# 8. 객체 리스트 정렬
### 1) python
```python
info_list = [('a', 10), ('b', 7), ('b', 8)]

# 1. 문자 사전순 정렬, 숫자 내림차순 정렬
info_list.sort(key=lambda x: (x[0], -x[1]))
```

### 2) java
#### 문자열의 경우 compareTo를 사용한다.
- -1 사전순
- 0 같다
- 1 사전역순

#### 숫자의 경우 compareTo가 없다.
- -1 오름차순
- 0 같다
- 1 내림차순

```java
ArrayList<Info> infoList = new ArrayList<>();
infoList.add(new Info("a", 10));
infoList.add(new Info("b", 7));
infoList.add(new Info("b", 8));

Collections.sort(infoList, (a, b) -> {
    // 문자가 같은 경우
    if(a.getName().compareTo(b.getName()) == 0) {
        // 숫자 내림차순 정렬
        return -(a.getAge() - b.getAge());
    }
    // 문자 사전순 정렬
    return a.getName().compareTo(b.getName());
});
```
