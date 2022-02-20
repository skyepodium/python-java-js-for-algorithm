# 1. 설명
- 날짜 형식을 변경하세요
```
Input: date = "1st Sep 2052"
Output: "2052-09-01"
```



[문제 링크](https://leetcode.com/problems/reformat-date/)


# 2. 코드
### 1) python
```python
class Solution:
    def reformatDate(self, date: str) -> str:
        # 1. init
        d = {"Jan": '01', "Feb": '02', "Mar": '03', "Apr": '04', "May": '05', "Jun": '06', "Jul": '07', "Aug": '08', "Sep": '09', "Oct": '10', "Nov": '11', "Dec": '12'}

        # 2. split
        day, month, year = date.split(" ")
        day = re.sub("[a-zA-Z]+", "", day)

        return f"{year}-{d[month]}-{day.zfill(2)}"
```

### 2) java
```java
class Solution {
    public String reformatDate(String date) {
        // 1. init
        Map<String, String> m = new HashMap<>();
        m.put("Jan", "01");
        m.put("Feb", "02");
        m.put("Mar", "03");
        m.put("Apr", "04");
        m.put("May", "05");
        m.put("Jun", "06");
        m.put("Jul", "07");
        m.put("Aug", "08");
        m.put("Sep", "09");
        m.put("Oct", "10");
        m.put("Nov", "11");
        m.put("Dec", "12");

        // 2. split
        String[] d = date.split(" ");
        String day = d[0].replaceAll("[a-zA-z]", "");

        return d[2] + "-" + m.get(d[1]) + "-" + zFill(day);
    }

    public String zFill(String strNum){
        return strNum.length() < 2 ? "0" + strNum : strNum;
    }
}
```