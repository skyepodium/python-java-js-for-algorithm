# 1. 설명
- 최대 길이 20인 수열이 주어집니다.
- 중복없이 만들수 있는 길이가 k인 수열의 조합을 구하세요.



[문제 링크](https://leetcode.com/problems/combinations/)

# 2. 코드
### 1) python
```python
class Solution:
    def combine(self, n: int, k: int) -> list[list[int]]:

        result = []

        def go(idx, stack, remain):
            if remain == 0:
                result.append(stack[:])
                return

            for i in range(idx + 1, n + 1):
                stack.append(i)
                go(i, stack, remain - 1)
                stack.pop()

        go(0, [], k)

        return result
```

### 2) java
```java
class Solution {

    List<List<Integer>> result = new ArrayList<>();
    int nVal = 0;
    public List<List<Integer>> combine(int n, int k) {

        nVal = n;

        go(0, k, new ArrayList<>());

        return result;
    }

    public void go(int idx, int remain, ArrayList<Integer> stack) {
        if(remain == 0) {
            result.add(new ArrayList<>(stack));
            return;
        }

        for(int i=idx; i< nVal; i++) {
            stack.add(i + 1);
            go(i + 1, remain - 1, stack);
            stack.remove(stack.size() - 1);
        }
    }
}
```