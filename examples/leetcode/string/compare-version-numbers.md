# 1. 설명
- 두 숫자의 버전을 비교하세요.


[문제 링크](https://leetcode.com/problems/compare-version-numbers/)


# 2. 코드
### 1) python
```python
class Solution:
    def compareVersion(self, version1: str, version2: str) -> int:
        # 0. exception
        if version1 == version2: return 0

        # 1. not_zero
        def not_zero(s):
            for idx, c in enumerate(s):
                if c != '0': return s[idx:]
            return 0

        # 2. split
        v1, v2 = version1.split("."), version2.split(".")

        # 3. len
        n, m = len(v1), len(v2)
        val = 1 if n > m else -1
        if val > 0 and n != m:
            for _ in range(abs(n-m)): v2.append('0')
        else:
            for _ in range(abs(n-m)): v1.append('0')

        # 4. loop
        for a, b in zip(v1, v2):
            a, b = int(not_zero(a)), int(not_zero(b))

            if a == b: continue
            elif a < b: return -1
            else: return 1

        return 0
```
