# 1. 설명
- 주어진 값과 같은 노드의 서브 트리를 반환하세요

[문제 링크](https://leetcode.com/problems/search-in-a-binary-search-tree/)

# 2. 코드
### 1) Python
```python
class Solution:
    def searchBST(self, root, val):
        
        if root and root.val > val: return self.searchBST(root.left, val)
        elif root and root.val < val: return self.searchBST(root.right, val)
        return root
```

### 2) Java
```java
class Solution {
    public TreeNode searchBST(TreeNode root, int val) {

        if(root != null && root.val > val) return searchBST(root.left, val);
        else if(root != null && root.val < val) return searchBST(root.right, val);
        return root;
    }
}
```

### 3) JavaScript
```js
const searchBST = (root, val) => {
    
    if(root && val < root.val) return searchBST(root.left, val)
    else if(root && val > root.val) return searchBST(root.right, val)
    return root
};
```

