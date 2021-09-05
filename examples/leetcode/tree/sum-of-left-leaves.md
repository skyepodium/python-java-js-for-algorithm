# 1. 설명
- 왼쪽 리프노드의 합을 구하세요.


[문제 링크](https://leetcode.com/problems/sum-of-left-leaves/)


# 2. 코드
### 1) python
```python
class Solution:
    def sumOfLeftLeaves(self, root: Optional[TreeNode]) -> int:
        # 1. init
        self.res = 0

        # 2. preorder
        def go(node, is_left):
            if not node:
                return

            if not node.left and not node.right and is_left:
                self.res += node.val

            go(node.left, True)
            go(node.right, False)

        go(root, False)

        return self.res
```

### 2) java
```java
class Solution {
    int res = 0;
    public int sumOfLeftLeaves(TreeNode root) {
        go(root, false);

        return res;
    }

    public void go(TreeNode node, Boolean isLeft) {
        if(node == null) return;

        if(node.left == null && node.right == null && isLeft) {
            res += node.val;
        }

        go(node.left, true);
        go(node.right, false);
    }
}
```