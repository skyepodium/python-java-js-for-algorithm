# 1. 설명
- 이진 탐색 트리의 노드들 중에서 k번째로 작은 값을 반환하세요


[문제 링크](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)


# 2. 코드
### 1) Python
```python
class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        # 1. init
        self.cnt = k
        self.res = -1
        
        # 2. search
        def search(node):
            if not node: return
            
            search(node.left)
            if node.val > self.res and self.cnt > 0:
                self.cnt -= 1
                self.res = node.val
            search(node.right)
            
        search(root)
        
        return self.res
```

### 2) Java
```java
class Solution {
    int cnt;
    int res;
    public int kthSmallest(TreeNode root, int k) {
        cnt = k;
        res = -1;

        search(root);

        return res;
    }

    public void search(TreeNode node) {
        if(node == null) return;

        search(node.left);
        if(node.val > res && cnt > 0) {
            cnt--;
            res = node.val;
        }
        search(node.right);
    }
}
```

### 3) JavaScript
```js
const kthSmallest = (root, k) => {
    let res = -1
    let cnt = k

    const search = (node) => {
        if(!node) return

        if(node.left) search(node.left)
        if(node.val > res && cnt > 0) {
            cnt--
            res = node.val
        }
        if(node.right) search(node.right)
    }

    search(root)

    return res
};
```