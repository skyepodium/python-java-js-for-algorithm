# 1. 설명
- 정수로 구성된 배열이 주어집니다.
- 모든 부분집합을 구하세요.



[문제 링크](https://leetcode.com/problems/subsets/)

# 2. 코드
### 1) python
```python
class Solution:
    def subsets(self, nums: list[int]) -> list[list[int]]:

        result = []
        size = len(nums)

        def go(idx, stack):
            result.append(stack[:])

            for i in range(idx, size):
                stack.append(nums[i])
                go(i + 1, stack)
                stack.pop()

        go(0, [])

        return result
```

### 2) java
```java
class Solution {

    int[] numsArr;
    int size;
    List<List<Integer>> result = new ArrayList<>();
    public List<List<Integer>> subsets(int[] nums) {

        numsArr = nums;
        size = nums.length;

        go(0, new ArrayList<>());

        return result;
    }

    public void go(int idx, List<Integer> stack) {
        result.add(new ArrayList<>(stack));

        for(int i=idx; i<size; i++) {
            stack.add(numsArr[i]);
            go(i + 1, stack);
            stack.remove(stack.size() - 1);
        }
    }
}
```