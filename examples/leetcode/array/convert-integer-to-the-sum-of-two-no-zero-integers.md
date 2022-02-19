# 1. 설명
- 두 수를 더해서 n이되는 쌍 1개를 구하세요.
- 단, 두 수는 0이 포함되면 안됩니다. 예) 10 x


[문제 링크](convert-integer-to-the-sum-of-two-no-zero-integers)

# 2. 코드
### 1) python
```python
class Solution:
    def getNoZeroIntegers(self, n: int) -> List[int]:
        return [[x, n-x] for x in range(1, n//2 + 1) if not "0" in str(x) and not "0" in str(n-x)][0]
```

### 2) java
```java
class Solution {
    public int[] getNoZeroIntegers(int n) {
        // 1. loop
        for(int i=1; i<=n/2 + 1; i++) {
            if(!nonZero(i) || !nonZero(n-i)) continue;

            return new int[]{i, n-i};
        }
        return new int[]{-1, -1};
    }

    // 2. nonZero
    public boolean nonZero(int num) {
        while(num > 0) {
            if(num % 10 == 0) return false;
            num /= 10;
        }
        return true;
    }
}
```