# 1. 설명
- 대소문자로 구성된 문자열에서 모음의 순서만 뒤집으세요


[문제 링크](https://leetcode.com/problems/reverse-vowels-of-a-string/)


# 2. 코드
### 1) python
```python
class Solution:
    def reverseVowels(self, s: str) -> str:
        # 1. init
        vowel_list = []
        vowel_set = set(list("aeiouAEIOU"))
        s_list = list(s)

        # 2. make vowel_list
        for idx, val in enumerate(s):
            if val in vowel_set:
                vowel_list.append(idx)

        # 3. loop
        l, r = 0, len(vowel_list) - 1
        while l < r:
            l_idx, r_idx = vowel_list[l], vowel_list[r]
            s_list[l_idx], s_list[r_idx] = s_list[r_idx], s_list[l_idx]
            l += 1
            r -= 1

        return "".join(s_list)
```

### 2) java
```java
class Solution {
    public String reverseVowels(String s) {
        // 1. init
        List<Integer> vowelList = new ArrayList<>();
        List<String> b = Arrays.stream("aeiouAEIOU".split("")).collect(Collectors.toList());
        Set<String> vowelSet = new HashSet<>(b);
        String[] sList = s.split("");

        // 2. make voewl_list
        for(int i=0; i<s.length(); i++) {
            String val = String.valueOf(s.charAt(i));
            if(vowelSet.contains(val)) vowelList.add(i);
        }

        // 3. loop
        int l = 0;
        int r = vowelList.size() - 1;

        while(l < r) {
            int lIdx = vowelList.get(l);
            int rIdx = vowelList.get(r);
            String temp = sList[lIdx];
            sList[lIdx] = sList[rIdx];
            sList[rIdx] = temp;
            l++;
            r--;
        }

        return String.join("",sList);
    }
}
```

### 3) JavaScript
```js
const reverseVowels = (s) => {
    // 1. init
    const vowelList = []
    const vowelSet = new Set("aeiouAEIOU".split(""))
    const sList = s.split("")

    // 2. make vowelList
    for(let i=0; i<s.length; i++) {
        const val = s[i]
        if(vowelSet.has(val)) vowelList.push(i)
    }

    // 3. loop
    let l = 0
    let r = vowelList.length - 1
    while(l < r) {
        const lIdx = vowelList[l], rIdx = vowelList[r]
        const temp = sList[lIdx]
        sList[lIdx] = sList[rIdx]
        sList[rIdx] = temp
        l++
        r--
    }

    return sList.join("")
};
```