# 1. 설명
- 공백으로 구분된 문자열이 주어집니다. 단어의 첫글자를 대문자로 변경해서 반환하세요

[문제 링크](https://www.hackerrank.com/challenges/capitalize/problem)

# 2. 코드
### 1) Python
파이썬 `capitalize()` 는 단어의 앞글자만 대문자로 변환합니다.
```python
def solve(s):
    return " ".join([c.capitalize() for c in s.split(" ")])
```