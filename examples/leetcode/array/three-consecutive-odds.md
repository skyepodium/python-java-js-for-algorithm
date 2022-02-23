# 1. 설명
- 배열에 홀수 3개가 연속으로 존재하는지 여부를 반환하세요.


[문제 링크](https://leetcode.com/problems/three-consecutive-odds/)


# 2. 코드
### 1) python
```python
class Solution:
    def threeConsecutiveOdds(self, arr: List[int]) -> bool:
        cnt = 0
        for i in range(len(arr)):
            if arr[i] & 1 == 0:
                cnt = 0
            else:
                cnt += 1
                if cnt >= 3: return True

        return False
```

### 2) java
```java
class Solution {
    public boolean threeConsecutiveOdds(int[] arr) {
        int cnt = 0;
        for(int i=0; i<arr.length; i++) {
            if((arr[i] & 1) == 0) cnt = 0;
            else {
                cnt++;
                if(cnt >+ 3) return true;
            }
        }
        return false;
    }
}
```