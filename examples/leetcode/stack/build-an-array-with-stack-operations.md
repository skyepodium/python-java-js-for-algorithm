# 1. 설명
- 스택 동작을 구현하세요


[문제 링크](https://leetcode.com/problems/build-an-array-with-stack-operations/)


# 2. 코드
### 1) python
```python
class Solution:
    def buildArray(self, target: List[int], n: int) -> List[str]:
        res = []
        max_val = max(target)
        idx = 0

        for t in range(1, n + 1):
            if t > max_val: break

            res.append("Push")
            if t is not target[idx]:
                res.append("Pop")
            else:
                idx += 1

        return res
```

### 2) java
```java
class Solution {
    public List<String> buildArray(int[] target, int n) {
        List<String> res = new ArrayList<>();
        int maxVal = Arrays.stream(target).max().getAsInt();
        int idx = 0;

        for(int i=1; i<=n; i++) {
            if(i > maxVal) break;

            res.add("Push");

            if(i != target[idx]) res.add("Pop");
            else idx++;
        }
        return res;
    }
}
```

### 3) JavaScript
```js
const buildArray = (target, n) => {
    const res = []
    const maxVal = Math.max(...target)
    let idx = 0

    for(let i=1; i<=n; i++) {
        if(i > maxVal) break

        res.push("Push")
        if(i !== target[idx]) res.push("Pop")
        else idx++
    }

    return res
};
```