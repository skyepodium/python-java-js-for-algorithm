# 1. 설명
- 3개의 노드로 구성된 바이너리 트리에서 자식 노드의 합과 부모 노드의 값이 같은지 여부를 반환하세요

[문제 링크](https://leetcode.com/problems/root-equals-sum-of-children/)

# 2. 코드
### 1) Python
```python
class Solution:
    def checkTree(self, root: Optional[TreeNode]) -> bool:
        return root.val == root.left.val + root.right.val
```

### 2) Java
```java
class Solution {
    public boolean checkTree(TreeNode root) {
        return root.val == root.left.val + root.right.val;        
    }
}
```

### 3) JavaScript
```js
const checkTree = (root) => {
    return root.val === root.left.val + root.right.val
};
```

