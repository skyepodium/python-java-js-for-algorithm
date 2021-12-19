# 1. 설명
- 트리의 직경을 구하세요.
- 직경은 node를 기준으로 왼쪽으로 제일 깊은 길이 + 오른쪽 제일 깊은 길이 입니다.
- 최대 직경은 root가 기준이 아닐 수 있습니다.

- 노드의 최대 개수: 10만



[문제 링크](https://leetcode.com/problems/diameter-of-binary-tree/)

# 2. 코드
### 1) python
```python
class Solution:
    result = 0

    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        def go(node):
            if not node:
                return 0

            left_depth = go(node.left)
            right_depth = go(node.right)

            self.result = max(self.result, left_depth + right_depth)

            return max(left_depth, right_depth) + 1

        go(root)

        return self.result
```

### 2) java
```java
class Solution {
    public int maxDiameter = 0;
    public int diameterOfBinaryTree(TreeNode root) {

        go(root);

        return maxDiameter;
    }

    public int go(TreeNode node) {
        if(node == null) return 0;

        int leftDepth = go(node.left);
        int rightDepth = go(node.right);

        this.maxDiameter = Math.max(this.maxDiameter, leftDepth + rightDepth);

        return Math.max(leftDepth, rightDepth) + 1;
    }
}
```