# 1. 설명
- 영문자만 대상으로 한다.
- 대소문자 구분하지 않는다.
- 금지된 단어는 제외한다.
- 가장 많이 언급된 단어를 반환하세요.

- 문자열의 길이 1 <= n <= 1000


[문제 링크](https://leetcode.com/problems/most-common-word/)


# 2. 코드
### 1) python
```python
import re
import collections


class Solution:
    def mostCommonWord(self, paragraph: str, banned: list[str]) -> str:
        # 1. 정규표현식으로 영문자가 아닌 문자 공백 1칸으로 변경
        paragraph = re.sub("[^a-zA-Z]", " ", paragraph).lower()

        # 2. 리스트 컴프리헨션으로 금지되지 않은 단어 저장
        words = [word for word in paragraph.split() if word not in banned]

        # 3. 단어의 개수 저장할 딕셔너리 생성
        count = collections.defaultdict(int)

        res = ""
        cnt = 0

        for word in words:
            count[word] += 1
            # 가장 많이 언급된 단어 갱신
            if count[word] > cnt:
                cnt = count[word]
                res = word

        return res
```

### 2) java
- set - 금지된 단어 저장
- map - 단어별 개수 저장
```java
class Solution {
    public String mostCommonWord(String paragraph, String[] banned) {
        // 1. 정규 표현식으로 영문자가 아닌 문자는 공백1칸으로 변경
        paragraph = paragraph.replaceAll("[^a-zA-Z]", " ");

        // 2. 한칸 이상의 공백을 기준으로 문자열 분리
        String[] p = paragraph.toLowerCase().split(" +");

        // 3. 금지된 단어를 저장할 set
        HashSet<String> s = new HashSet<String>();
        for(String word: banned) {
            s.add(word);
        }

        // 4. 개수를 검사할 map
        HashMap<String, Integer> map = new HashMap<String, Integer>();

        String result = "";
        int cnt = 0;

        for(String word: p) {
            // 금지된 단어 패스
            if(s.contains(word)) continue;

            // 없으면 개수 1체크
            if(!map.containsKey(word)) {
                map.put(word, 1);
            }
            // 있으면 개수 1 증가
            else {
                int cur_cnt = map.get(word);
                map.put(word, cur_cnt + 1);
            }

            // 개수 갱신, 제일 많은 단어 갱신
            if(map.get(word) > cnt) {
                result = word;
                cnt = map.get(word);
            }
        }

        return result;
    }
}
```