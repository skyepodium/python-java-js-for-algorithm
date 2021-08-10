# 1. 설명
- 정수로 구성된 배열이 주어집니다.
- 중복을 포함해서 만든 조합의 합이 target과 같아지는 조합을 모두 구하세요.



[문제 링크](https://leetcode.com/problems/combination-sum/)

# 2. 코드
### 1) python
```python
class Solution:
    def combinationSum(self, candidates: list[int], target: int) -> list[list[int]]:

        result = []

        size = len(candidates)

        def go(idx, sumVal, stack):
            if sumVal >= target:
                if sumVal == target:
                    result.append(stack[:])
                return

            for i in range(idx, size):
                stack.append(candidates[i])
                go(i, sumVal + candidates[i], stack)
                stack.pop()

        go(0, 0, [])

        return result
```

### 2) java
```java
class Solution {
    List<List<Integer>> result = new ArrayList<>();
    int targetVal = 0;
    int[] cData;
    int size = 0;
    public List<List<Integer>> combinationSum(int[] candidates, int target) {

        targetVal = target;
        cData = candidates;
        size = candidates.length;

        go(0, 0, new ArrayList<>());

        return result;
    }

    public void go(int idx, int sumVal, List<Integer> stack) {
        if(sumVal >= targetVal) {
            if(sumVal == targetVal) {
                result.add(new ArrayList<>(stack));
            }
            return;
        }

        for(int i=idx; i<size; i++) {
            stack.add(cData[i]);
            go(i, sumVal + cData[i], stack);
            stack.remove(stack.size() - 1);
        }
    }
}
```