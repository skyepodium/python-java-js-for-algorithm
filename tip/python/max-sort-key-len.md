# max, sort key len

# 1. 내용
max, sort에는 key 옵션을 줄 수 있고, key에 len 옵션을 줄 수도 있습니다.

길이 따라 최대값을 반환하거나, 길어지는 순으로 정렬할 수 있습니다.


# 2. 코드
### 1) max
```python
l = ["a", "ab", "abcde", "d", "q"]

res = max(l, key=len)

print('res', res)
# res abcde
```

### 2) sort
```python
l = ["a", "ab", "abcde", "d", "q"]

l.sort(key=len)

print('l', l)
# l ['a', 'd', 'q', 'ab', 'abcde']
```