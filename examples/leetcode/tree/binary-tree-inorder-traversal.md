# 1. 설명
- 중위 순회(inorder) 결과를 반환하세요.
- left, mid, right


[문제 링크](https://leetcode.com/problems/binary-tree-inorder-traversal/)


# 2. 코드
### 1) python
```python
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        # 1. exception
        if not root:
            return []

        # 2. init
        res = []

        # 3. inorder
        def go(node):
            if not node:
                return

            go(node.left)
            res.append(node.val)
            go(node.right)

        go(root)

        return res 
```

### 2) java
```java
class Solution {
    List<Integer> res = new ArrayList<>();
    public List<Integer> inorderTraversal(TreeNode root) {
        // 1. exception
        if(root == null) return res;

        // 2. inorder
        inOrder(root);

        return res;
    }

    public void inOrder(TreeNode node) {
        if(node == null) return;

        inOrder(node.left);
        res.add(node.val);
        inOrder(node.right);
    }
}
```