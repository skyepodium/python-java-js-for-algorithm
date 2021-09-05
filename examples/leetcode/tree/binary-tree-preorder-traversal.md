# 1. 설명
- 전위 순회(preorder) 결과를 반환하세요.
- root, left, right


[문제 링크](https://leetcode.com/problems/binary-tree-preorder-traversal/)


# 2. 코드
### 1) python
```python
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        # 1. init
        res = []

        # 2. exception
        if not root:
            return res

        # 3. pre_order
        def pre_order(node):
            if not node:
                return

            res.append(node.val)
            pre_order(node.left)
            pre_order(node.right)

        pre_order(root)

        return res
```

### 2) java
```java
class Solution {
    List<Integer> res = new ArrayList<>();
    public List<Integer> preorderTraversal(TreeNode root) {
        // 1. exception
        if(root == null) return res;

        // 2. preOrder
        preOrder(root);

        return res;
    }

    public void preOrder(TreeNode node) {
        if(node == null) return;

        res.add(node.val);
        preOrder(node.left);
        preOrder(node.right);
    }
}
```