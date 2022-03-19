# 1. 설명
- 반환 순서는 상관없다.
- anagram별로 그룹화 해서 반환하세요

- 배열의 길이 1 <= n <= 10만
- 문자열의 길이 1 <= m <= 100


[문제 링크](https://leetcode.com/problems/group-anagrams/)


# 2. 코드
### 1) python
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        # 1. init
        d = defaultdict(list)

        # 2. loop
        for idx, s in enumerate(strs):
            d["".join(sorted(s))].append(s)

        return d.values()
```

### 2) java
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {

        // 1. 결과를 저장할 ArrayList
        List<List<String>> result = new ArrayList<>();

        // 2. 인덱스를 저장할 map
        HashMap<String, Integer> m = new HashMap<>();
        int idx = 0;

        for(String word: strs) {
            // 3. 정렬
            char[] charArray = word.toCharArray();
            Arrays.sort(charArray);
            String sortedString = new String(charArray);

            int cur_idx = 0;
            // 4. map에 정렬된 값이 있으면 ArrayList의 해당 인덱스에 추가
            if(m.containsKey(sortedString)) {
                cur_idx = m.get(sortedString);
                List<String> cur = result.get(cur_idx);
                cur.add(word);
                result.set(cur_idx, cur);
             }
            // 5. map에 정렬된 값이 없으면, 새로운 ArrayList 추가
            else {
                cur_idx = idx;
                m.put(sortedString, cur_idx);
                idx++;
                List<String> cur = new ArrayList<>();
                cur.add(word);
                result.add(cur);
            }
        }
        return result;
    }
}
```

### 3. JavaScript
```js
var groupAnagrams = function(strs) {
    // 1. init
    const m = new Map()

    // 2. loop
    strs.forEach(s => {
        const key = s.split("")
            .sort((a, b) => a.localeCompare(b))
            .join("")
        m.has(key) ? m.set(key, m.get(key).concat([s])) : m.set(key, [s])
    })

    return [...m.values()]
};
```