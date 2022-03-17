# 1. 설명
- y와 p의 개수의 동일여부를 반환하세요.


[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12916)

# 2. 코드
### 1) python
```python
def solution(s):
    return len(s.lower().split("p")) == len(s.lower().split("y"))
```

### 2) java
```java
class Solution {
    boolean solution(String s) {
        // 1. init
        s = s.toLowerCase();
        int cnt = 0;
        
        // 2. loop
        for(int i=0; i<s.length(); i++) {
            char cur = s.charAt(i);
            if(cur == 'p') cnt++;
            else if(cur == 'y') cnt--;
        }
        
        return cnt == 0;
    }
}
```

### 3) JavaScript
```js
function solution(s){
    return s.toLowerCase().split("p").length === s.toLowerCase().split("y").length
}
```
