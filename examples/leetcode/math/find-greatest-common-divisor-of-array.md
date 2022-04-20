# 1. 설명
- 최대공약수를 구하세요


[문제 링크](https://leetcode.com/problems/find-greatest-common-divisor-of-array/)

# 2. 코드
### 1) Python
```python
class Solution:
    def findGCD(self, nums: List[int]) -> int:

        def gcd(a, b):
            if b == 0:
                return a
            else:
                return gcd(b, a % b)

        return gcd(min(nums), max(nums))
```

### 2) Java
```java
class Solution {
    public int findGCD(int[] nums) {

        return gcd(Arrays.stream(nums).min().getAsInt(), Arrays.stream(nums).max().getAsInt());
    }

    public int gcd(int a, int b) {
        if(b == 0) return a;
        else return gcd(b, a%b);
    }
}
```

### 3) JavaScript
```js
const findGCD = (nums) => {

    const gcd = (a, b) => {
        if(b === 0) return a
        else return gcd(b, a%b)
    }

    return gcd(Math.min(...nums), Math.max(...nums))
};
```