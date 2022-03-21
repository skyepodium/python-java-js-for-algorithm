# 1. 설명
- 룰에 맞는 아이템의 개수를 구하세요.


[문제 링크](https://leetcode.com/problems/count-items-matching-a-rule/)

# 2. 코드
### 1) python
```python
class Solution:
    def countMatches(self, items: List[List[str]], ruleKey: str, ruleValue: str) -> int:
        # 1. init
        d = {
            "type": 0,
            "color": 1,
            "name": 2
        }
        res = 0
        
        # 2. loop
        for i in items:
            if i[d[ruleKey]] == ruleValue:
               res += 1
            
        return res
```

### 2) java
```java
class Solution {
    public int countMatches(List<List<String>> items, String ruleKey, String ruleValue) {
        // 1. init
        Map<String, Integer> d = new HashMap<>();
        d.put("type", 0);
        d.put("color", 1);
        d.put("name", 2);
        int res = 0;

        // 2. loop
        for(List<String> i: items) {
            if(i.get(d.get(ruleKey)).equals(ruleValue)) res++;
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const countMatches = (items, ruleKey, ruleValue) => {
    // 1. init
    let res = 0
    const d = new Map()
    d.set("type", 0)
    d.set("color", 1)
    d.set("name", 2)

    // 2. loop
    items.forEach(i => {
        if(i[d.get(ruleKey)] === ruleValue) res++
    })

    return res
};
```