# 1. 설명
- 야구 게임을 구현하세요

[문제 링크](https://leetcode.com/problems/baseball-game/)


# 2. 코드
### 1) python
```python
class Solution:
    def calPoints(self, ops: List[str]) -> int:
        # 1. init
        s = []
        sum_val = 0

        # 2. loop
        for o in ops:
            if o == 'C':
                if len(s) > 0:
                    sum_val -= s[-1]
                    s.pop()
            elif o == 'D':
                val = s[-1] * 2
                sum_val += val
                s.append(val)
            elif o == '+':
                val = s[-1] + s[-2]
                sum_val += val
                s.append(val)
            else:
                val = int(o)
                sum_val += val
                s.append(val)
                
        return sum_val
```

### 2) java
```java
class Solution {
    public int calPoints(String[] ops) {
        // 1. init
        Stack<Integer> s = new Stack<>();
        int sumVal = 0;

        // 2. loop
        for(String o: ops) {
            if(o.equals("C")) {
                if(s.size() > 0) {
                    sumVal -= s.pop();
                }
            }
            else if(o.equals("D")) {
                int val = s.peek() * 2;
                sumVal += val;
                s.add(val);
            }
            else if(o.equals("+")) {
                int val = s.peek() + s.get(s.size()-2);
                sumVal += val;
                s.add(val);
            }
            else {
                int val = Integer.parseInt(o);
                sumVal += val;
                s.add(val);
            }
        }

        return sumVal;
    }
}
```

### 3) JavaScript
```js
const calPoints = (ops) => {
    // 1. init
    const s = []
    let sumVal = 0

    // 2. loop
    ops.forEach(o => {
        if(o === 'C') {
            if(o.length > 0) {
                sumVal -= s.pop()
            }
        }
        else if(o === 'D') {
            const val = s[s.length - 1] * 2
            sumVal += val
            s.push(val)
        }
        else if(o === '+') {
            const val = s[s.length - 1] + s[s.length - 2]
            sumVal += val
            s.push(val)
        }
        else {
            const val = Number(o)
            sumVal += val
            s.push(val)
        }
    })

    return sumVal
};
```