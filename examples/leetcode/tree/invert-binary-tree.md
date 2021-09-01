# 1. 설명
- 중심을 기준으로 이진 트리를 뒤집으세요.


[문제 링크](https://leetcode.com/problems/invert-binary-tree/)


# 2. 코드
### 1) python
```python
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if root:
            root.left, root.right = self.invertTree(root.right), self.invertTree(root.left)

        return root 
```

### 2) java
```java
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if(root != null) {
            TreeNode temp = null;
            temp = root.left;
            root.left = invertTree(root.right);
            root.right = invertTree(temp);
        }

        return root;
    }
}
```