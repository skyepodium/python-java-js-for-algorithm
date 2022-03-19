# 정규 표현식

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