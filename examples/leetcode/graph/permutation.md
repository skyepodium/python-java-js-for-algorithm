# 1. 설명
- 정수로 구성된 배열이 주어집니다.
- 배열의 원소로 중복없이 순열을 만드세요.



[문제 링크](https://leetcode.com/problems/permutations/)

# 2. 코드
### 1) python
```python
class Solution:
    def permute(self, nums: list[int]) -> list[list[int]]:

        result = []
        size = len(nums)
        check = [False for _ in range(21)]

        def go(idx, stack):
            if idx >= size:
                result.append(list(stack))
                return

            for num in nums:
                if not check[num+10]:
                    check[num+10] = True
                    stack.append(num)

                    go(idx + 1, stack)

                    check[num+10] = False
                    stack.pop()

        go(0, [])

        return result
```

### 2) java
```java
class Solution {

    int size = 0;
    int[] check;
    int[] curNums;
    List<List<Integer>> result;
    public List<List<Integer>> permute(int[] nums) {

        size = nums.length;
        check = new int[21];
        curNums = nums;

        result = new ArrayList<>();

        go(0, new ArrayList<>());

        System.out.println(result.get(0));
        return result;
    }

    public void go(int idx, ArrayList<Integer> stack) {
        if(idx >= size) {
            result.add(new ArrayList<>(stack));
            return;
        }

        for(int num: curNums) {
            if(check[num + 10] == 0) {
                check[num+10] = 1;
                stack.add(num);

                go(idx + 1, stack);

                check[num+10] = 0;
                stack.remove(stack.size() - 1);
            }
        }
    }
}
```