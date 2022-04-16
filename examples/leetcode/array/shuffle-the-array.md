# 1. 설명
- 배열 2개를 셔플하세요


[문제 링크](https://leetcode.com/problems/shuffle-the-array/)

# 2. 코드
### 1) Python
```python

```

### 2) Java
```java

```

### 3) JavaScript
```js
const shuffle = (nums, n) => {
    function* zip(a, b) {
        const n = Math.min(a.length, b.length)

        for(let i=0; i<n; i++) {
            yield [a[i], b[i]]
        }
    }
    return [...zip(nums.slice(0, n), nums.slice(n))].flatMap(x => x)
};
```