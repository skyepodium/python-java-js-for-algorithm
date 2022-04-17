# 1. 설명
- BST 리프노트 까지의 binary 합을 구하세요

[문제 링크](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/)

# 2. 코드
### 1) Python
```python
class Solution:
    res = 0
    def sumRootToLeaf(self, root: Optional[TreeNode]) -> int:
        # 1. init
        self.res = 0
        
        # 2. dfs
        def dfs(node, val):
            if not node: return
            
            if not node.left and not node.right:
                self.res += int(f"{val}{node.val}", 2)
                return

            dfs(node.left, f"{val}{node.val}")
            dfs(node.right, f"{val}{node.val}")

        dfs(root, "")

        return self.res
```

### 2) Java
```java
class Solution {
    public int res = 0;
    public int sumRootToLeaf(TreeNode root) {
        // 1. init
        res = 0;

        // 2. dfs
        dfs(root, "");

        return this.res;
    }

    public void dfs(TreeNode node, String val) {
        if(node == null) return;

        if(node.left == null && node.right == null) {
            this.res += binaryToInt(String.format("%s%s", val, node.val));
            return;
        }

        dfs(node.left, String.format("%s%s", val, node.val));
        dfs(node.right, String.format("%s%s", val, node.val));
    }

    public int binaryToInt(String b) {
        int res = 0;

        for(int i=0; i<b.length(); i++) {
            res *= 2;
            if(b.charAt(i) == '1') res += 1;
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const sumRootToLeaf = (root) => {
    // 1. init
    let res = 0

    // 2. binaryToInt
    const binaryToInt = b => {
        let res = 0;

        for(let i=0; i<b.length; i++) {
            res *= 2;
            if(b[i] === '1') res += 1
        }

        return res;
    }

    // 3. dfs
    const dfs = (node, val) => {
        if(!node) return

        if(!node.left && !node.right) {
            res += binaryToInt(`${val}${node.val}`)
            return
        }

        dfs(node.left, `${val}${node.val}`)
        dfs(node.right, `${val}${node.val}`)
    }

    dfs(root, "")

    return res
};
```

