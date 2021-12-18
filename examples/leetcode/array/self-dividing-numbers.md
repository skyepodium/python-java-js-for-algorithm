# 1. 설명
- self dividing number 여부를 반환하세요.

- 1 <= left, right <= 1만



[문제 링크](https://leetcode.com/problems/self-dividing-numbers/)

# 2. 코드
### 1) python
```python
class Solution:
    def selfDividingNumbers(self, left: int, right: int) -> List[int]:
        # 1. check
        def check(num):
            str_num = str(num)

            if '0' in str_num:
                return False

            for a in str_num:
                if num % int(a) != 0:
                    return False

            return True

        # 2. list comprehension
        return [x for x in range(left, right+1) if check(x)]
```

### 2) java
```java
class Solution {
    public List<Integer> selfDividingNumbers(int left, int right) {

        return IntStream.range(left, right + 1)
                        .filter(this::check)
                        .boxed()
                        .collect(Collectors.toList());
    }

    public boolean check(int num) {
        String strNum = Integer.toString(num);

        for(int i=0; i<strNum.length(); i++) {
            char cur = strNum.charAt(i);

            if(cur == '0') return false;

            if(num % ((int)cur - (int)'0') != 0) return false;
        }
        return true;
    }
}
```