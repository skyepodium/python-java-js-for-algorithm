# 1. 설명
- 두 트리가 동일한지를 반환하세요

[문제 링크](https://leetcode.com/problems/same-tree/)


# 2. 코드
### 1) python
```python

```

### 2) java
```java

```

### 3) JavaScript
```js
const isSameTree = (p, q) => {
    if(!p && !q) return true
    if(!p || !q) return false
    if(p?.val === q?.val) return isSameTree(p.left, q.left) && isSameTree(p.right, q.right)

    return false
};
```