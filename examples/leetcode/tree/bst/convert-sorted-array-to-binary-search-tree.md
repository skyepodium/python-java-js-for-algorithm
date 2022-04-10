# 1. 설명
- 정렬된 배열을 BST로 변경하세요

[문제 링크](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

# 2. 코드
### 1) Python
```python
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        # 0. exception
        if not nums: return None
        
        # 1. init
        mid = len(nums) // 2
        
        # 2. make tree
        node = TreeNode(nums[mid])
        node.left = self.sortedArrayToBST(nums[:mid])
        node.right = self.sortedArrayToBST(nums[mid+1:])
        
        return node
```

### 2) Java
```java
class Solution {
    public TreeNode sortedArrayToBST(int[] nums) {
        // 1. exception
        if(nums.length < 1) return null;

        // 2. mid
        int mid = nums.length / 2;

        // 3. make tree
        TreeNode node = new TreeNode(nums[mid]);
        node.left = this.sortedArrayToBST(Arrays.copyOfRange(nums, 0, mid));
        node.right = this.sortedArrayToBST(Arrays.copyOfRange(nums, mid + 1, nums.length));

        return node;
    }
}
```

### 3) JavaScript
```js

```

