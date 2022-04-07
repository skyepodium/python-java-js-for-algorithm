# 1. 설명
- 배열의 곱 결과가 양수면 1, 음수면 -1, 0이면 0을 반환하세요



[문제 링크](https://leetcode.com/problems/sign-of-the-product-of-an-array/)

# 2. 코드
### 1) python
```python
class Solution:
    def arraySign(self, nums: List[int]) -> int:
        res = 1

        for num in nums:
            if num == 0: res = 0
            elif num < 0: res *= -1

        return res
```

### 2) java
```java
class Solution {
    public int arraySign(int[] nums) {
        int res = 1;

        for(int num: nums) {
            if(num == 0) res = 0;
            else if(num < 0) res *= -1;
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const arraySign = (nums) => {
    let res = 1

    nums.forEach(x => {
        if(x === 0) res = 0
        else if(x < 0) res *= -1
    })

    return res
};
```

### 4) Kotlin
```kt
class Solution {
    fun arraySign(nums: IntArray): Int {
        var res:Int = 1

        for(num in nums) {
            if(num == 0) res = 0
            else if(num < 0) res *= -1
        }

        return res
    }
}
```