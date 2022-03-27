# 1. 설명
- row를 약한순으로 정렬하고 k개 반환하세요.


[문제 링크](https://leetcode.com/problems/the-k-weakest-rows-in-a-matrix/)


# 2. 코드
### 1) Python
```python
```

### 2) Java
```java

```

### 3) JavaScript
```js
const kWeakestRows = (mat, k) => {
    return mat.map((x, idx) => [x.reduce((prev, cur) => prev + cur), idx])
        .sort((a, b) => a[0] - b[0])
        .map(x => x[1])
        .slice(0, k)
};
```

