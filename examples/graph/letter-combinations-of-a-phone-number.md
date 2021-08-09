# 1. 설명
- 최대 길이 4의 숫자로 구성된 문자열이 주어집니다.
- 번호를 눌러서 만들 수 있는 모든 단어의 조합을 구하세요.



[문제 링크](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

# 2. 코드
### 1) python
```python
class Solution:
    def letterCombinations(self, digits: str) -> list[str]:

        nums = [
            "",
            "",
            "abc",
            "def",
            "ghi",
            "jkl",
            "mno",
            "pqrs",
            "tuv",
            "wxyz"
        ]

        result = []
        size = len(digits)

        def go(idx, val):
            if idx >= size:
                if len(val) > 0:
                    result.append("".join(val))
                return

            cur = int(digits[idx])

            for num in nums[cur]:
                val.append(num)
                go(idx + 1, val)
                val.pop()

        go(0, [])

        return result
```

### 2) java
```java
class Solution {

    int size = 0;
    List<String> result = new ArrayList<>();
    String[] nums = {
            "",
            "",
            "abc",
            "def",
            "ghi",
            "jkl",
            "mno",
            "pqrs",
            "tuv",
            "wxyz"
    };
    String digitsStr = "";

    public List<String> letterCombinations(String digits) {

        digitsStr = digits;
        size = digitsStr.length();

        go(0, "");

        return result;
    }

    public void go(int idx, String val) {
        if(idx >= size) {
            if(val.length() > 0) {
                result.add(val);
            }
            return;
        }

        int cur = Integer.parseInt(String.valueOf(digitsStr.charAt(idx)));
        String curNums = nums[cur];
        int size = curNums.length();

        for(int i=0; i<size; i++) {
            val += curNums.charAt(i);
            go(idx + 1, val);
            val = val.substring(0, val.length() - 1);
        }
    }
}
```