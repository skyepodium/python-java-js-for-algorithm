# 1. 설명
- 각 문자열의 첫번째는 identifier이다.

- letter-logs - 영소문자로 구성되어있다.
- digit-logs - 숫자로 구성되어 있다.

- letter-logs는 digit-logs 이후에 온다.
- letter-logs는 사전순으로 정렬한다. 만약 같으면 identifier의 사전순으로 정렬한다.
- digit-logs는 현 순서를 유지한다.


[문제 링크](https://leetcode.com/problems/reorder-data-in-log-files/)


# 2. 코드
### 1) python
```python
class Solution:
    def reorderLogFiles(self, logs: list[str]) -> list[str]:
        
        letters = []
        digits = []
        
        for log in logs:
            # 1. identifier를 제외한 content가 숫자이면
            if log.split(" ")[1].isdigit():
                digits.append(log)
            # 2. content가 문자이면
            else:
                letters.append(log)
                
        # 3. letters를 사전순으로 정렬한다. 만약 같으면 identifier 사전순으로 정렬한다.      
        letters.sort(key=lambda x: (x.split(" ")[1:], x.split(" ")[0]))                
        # 4. letters 이후에 digits가 온다.
        return letters + digits
        
```

### 2) java
```java
class Solution {
    public String[] reorderLogFiles(String[] logs) {

        ArrayList<String> letters = new ArrayList<>();
        ArrayList<String> digits = new ArrayList<>();

        for(String log: logs) {
            String[] splitLog = log.split(" ");

            // 1. identifier를 제외한 content가 숫자인 경우
            if(isDigit(splitLog[1])) digits.add(log);

            // 2. content가 문자인 경우
            else letters.add(log);
        }

        // 3. letters 사전 순 정렬, 만약 같으면 identifier 사전 순 정렬
        Collections.sort(letters, (a, b) -> {
            String first = a.split(" ", 2)[1];
            String second = b.split(" ", 2)[1];

            if(first.equals(second)) {
                return a.split(" ")[0].compareTo(b.split(" ")[0]);
            }
            else{
                return first.compareTo(second);
            }
        });

        // 4. 결과 String Array로 반환
        letters.addAll(digits);
        String[] result = new String[letters.size()];
        return letters.toArray(result);
    }

    public Boolean isDigit(String s) {
        int size = s.length();
        for(int i=0; i<size; i++) {
            if(!Character.isDigit(s.charAt(i))) return false;
        }
        return true;
    }
}
```