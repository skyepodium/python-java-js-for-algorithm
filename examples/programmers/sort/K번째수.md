# 1. 설명
규칙
- array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
- 1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
- 2에서 나온 배열의 3번째 숫자는 5입니다.

규칙에 따라 숫자를 반환하세요

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42748)


# 2. 코드
### 1) python
```python
def solution(array, commands):
    return [sorted(array[s - 1:e])[n - 1] for s, e, n in commands]
```

### 2) java
```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] array, int[][] commands) {
        // 1. init
        int[] answer = new int[commands.length];
        int idx = 0;
        
        // 2. loop
        for(int[] c: commands) {
            // 배열 자르기 - Arrays.copyOfRange 사용
            int[] t = Arrays.copyOfRange(array, c[0]-1, c[1]);
            Arrays.sort(t);
            answer[idx++] = t[c[2]-1];    
        }

        return answer;
    }
}
```

### 3) javascritp
```js
function solution(array, commands) {
    return commands.map(c => array.slice(c[0]-1, c[1]).sort((a,b) => a - b)[c[2]-1])
}
```