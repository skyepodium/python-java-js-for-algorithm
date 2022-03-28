# 1. 설명
- 이진 탐색 트리의 노드들 중에서 k번째로 작은 값을 반환하세요


[문제 링크](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)


# 2. 코드
### 1) Python
```python
class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        res = []

        def go(node):
            res.append(node.val)
            if node.left:
                go(node.left)
            if node.right:
                go(node.right)

        go(root)

        return sorted(res)[k-1]
```

### 2) Java
```java
class Solution {
    List<Integer> res;

    public int kthSmallest(TreeNode root, int k) {
        
        res = new ArrayList<>();

        search(root);

        res.sort(Comparator.naturalOrder());

        return res.get(k - 1);
    }

    public void search(TreeNode node) {
        res.add(node.val);

        if(node.left != null) search(node.left);
        if(node.right != null) search(node.right);
    }
}
```

### 3) JavaScript
```js
const kthSmallest = (root, k) => {
    const res = []

    const search = (node) => {
        res.push(node.val)

        if(node.left) search(node.left)
        if(node.right) search(node.right)
    }

    search(root)

    res.sort((a, b) => a - b)

    return res[k-1]
};
```