# split maxsplit

# 1. 내용
문자열을 `split`하면 모든 문자열이 split 되어 리스트가 반환됩니다.

필요한 만큼만 분할하기 위해 maxsplit 옵션을 사용합니다.


# 2. 코드
```python
import re

s = "a    b  c d"

res = re.split(" +", s, maxsplit=1)

print('res', res)
# res ['a', 'b  c d']
```