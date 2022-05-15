# 1. 설명
- 리프노드의 합을 구하세요


[문제 링크](https://leetcode.com/problems/deepest-leaves-sum/)


# 2. 코드
### 1) Python
```python
class Solution:
    def deepestLeavesSum(self, root: Optional[TreeNode]) -> int:
        # 1. init
        self.d = 0
        self.res = 0

        # 2. dfs
        def dfs(node, depth):
            if depth == self.d:
                self.res += node.val

            if depth > self.d:
                self.d = depth
                self.res = node.val

            for n_node in [node.left, node.right]:
                if not n_node: continue
                dfs(n_node, depth + 1)

        dfs(root, 0)

        return self.res
```

### 2) Java
```java
class Solution {
    int d = 0;
    int res = 0;
    public int deepestLeavesSum(TreeNode root) {
        dfs(root, 0);

        return res;
    }

    public void dfs(TreeNode node, int depth) {
        if(node == null) return;

        if(depth == this.d) this.res += node.val;

        if(depth > this.d) {
            this.res = node.val;
            this.d = depth;
        }

        dfs(node.left, depth + 1);
        dfs(node.right, depth + 1);
    }
}
```

### 3) JavaScript
```js
const deepestLeavesSum = (root) => {
    // 1. init
    let d = 0
    let res = 0

    // 2. dfs
    const dfs = (node, depth) => {
        if(!node) return

        if(depth === d) res += node.val

        if(depth > d) {
            res = node.val
            d = depth
        }

        dfs(node.left, depth + 1)
        dfs(node.right, depth + 1)
    }

    dfs(root, 0)

    return res
};
```

### 4) TypeScript
```ts
const deepestLeavesSum = (root: TreeNode | null): number => {
    // 1. init
    let d: number = 0
    let res: number = 0

    // 2. dfs
    const dfs = (node: TreeNode, depth: number) => {
        if(!node) return

        if(depth === d) res += node.val

        if(depth > d) {
            res = node.val
            d = depth
        }

        dfs(node.left, depth + 1)
        dfs(node.right, depth + 1)
    }

    dfs(root, 0)

    return res
};
```