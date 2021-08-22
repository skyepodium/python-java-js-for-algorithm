# 1. 설명
- 더 따뜻한 날씨는 며칠을 기다려야 오는지 구하세요.


[문제 링크](https://leetcode.com/problems/daily-temperatures/)

# 2. 코드
### 1) python
```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        # 1. init
        stack = []
        res = [0 for _ in range(len(temperatures))]
        
        # 2. loop
        for i in range(len(temperatures)):
            cur = temperatures[i]
            
            while stack and temperatures[stack[-1]] < cur:
                top = stack.pop()
                res[top] = i - top
            
            stack.append(i)
                
        return res
```

### 2) java
```java
import java.util.Stack;

class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        // 1. init
        int size = temperatures.length;
        int[] res = new int[size];
        Stack<Integer> s = new Stack<>();

        // 2. loop
        for(int i=0; i<size; i++) {
            int cur = temperatures[i];
            while(!s.empty() && temperatures[s.peek()] < cur) {
                int top = s.pop();
                res[top] = i - top;
            }

            s.add(i);
        }

        return res;
    }
}
```