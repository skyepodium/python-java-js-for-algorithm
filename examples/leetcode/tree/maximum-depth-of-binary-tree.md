# 1. 설명
- 트리의 최대 깊이를 구하세요.


[문제 링크](https://leetcode.com/problems/maximum-depth-of-binary-tree/)


# 2. 코드
### 1) python
```python
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        # 1. init
        self.res = 0
        
        # 2. dfs
        def dfs(node, cnt):
            if not node:
                return
            
            self.res = max(self.res, cnt)
            dfs(node.left, cnt + 1)
            dfs(node.right, cnt + 1)
        
        dfs(root, 1)
        
        return self.res
```

### 2) Java
```java
class Solution {
    int res = 0;
    public int maxDepth(TreeNode root) {
        // 1. exception
        if(root == null) return 0;
        
        // 2. dfs
        dfs(root, 1);
        
        return res;
    }
    
    public void dfs(TreeNode root, int cnt) {
        if(root == null) return;
        
        if(root.left == null && root.right == null) {
            res = Math.max(res, cnt);
        }
        
        dfs(root.left, cnt + 1);
        dfs(root.right, cnt + 1);
        
    }
}
```

### 3) JavaScript
```js
const maxDepth = (root) => {
    // 1. init
    let res = 0

    // 2. dfs
    const dfs = (node, cnt) => {
        if(!node) return

        res = Math.max(res, cnt)
        dfs(node.left, cnt + 1)
        dfs(node.right, cnt + 1)
    }

    dfs(root, 1)

    return res
};
```