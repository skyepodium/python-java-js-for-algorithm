# 1. 설명
트리의 대칭 여부를 반환하세요


[문제 링크](https://leetcode.com/problems/symmetric-tree/)


# 2. 코드
### 1) Python
```python
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:

        def go(a, b):
            if not a and not b: return True

            if not a and b: return False
            if a and not b: return False

            if a.val != b.val: return False

            return go(a.left, b.right) and go(a.right, b.left)

        return go(root, root)

```

### 2) Java
```java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        
        return go(root, root);
    }

    public boolean go(TreeNode a, TreeNode b) {
        if(a == null && b == null) return true;
        else if(a != null && b == null) return false;
        else if(a == null && b != null) return false;

        if(a.val != b.val) return false;

        return go(a.left, b.right) && go(a.right, b.left);
    }
}
```

### 3) JavaScript
```js
const isSymmetric = root => {

    const go = (a, b) => {
        if(!a && !b) return true
        else if(a && !b) return false
        else if(!a && b) return false

        if(a.val !== b.val) return false

        return go(a.left, b.right) && go(a.right, b.left)
    }

    return go(root, root)
};
```
