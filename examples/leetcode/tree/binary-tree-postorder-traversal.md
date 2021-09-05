# 1. 설명
- 후위 순회(postorder) 결과를 반환하세요.
- left, right, root


[문제 링크](https://leetcode.com/problems/binary-tree-postorder-traversal/)


# 2. 코드
### 1) python
```python
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        # 1. init
        res = []

        # 2. exception
        if not root:
            return res

        # 3. post_order
        def post_order(node):
            if not node:
                return

            post_order(node.left)
            post_order(node.right)
            res.append(node.val)

        post_order(root)

        return res
```

### 2) java
```java
class Solution {
    List<Integer> res = new ArrayList<>();
    public List<Integer> postorderTraversal(TreeNode root) {
        // 1. exception
        if(root == null) return res;

        // 2. postOrder
        postOrder(root);

        return res;
    }

    public void postOrder(TreeNode node) {
        if(node == null) return;

        postOrder(node.left);
        postOrder(node.right);
        res.add(node.val);

    }
}
```