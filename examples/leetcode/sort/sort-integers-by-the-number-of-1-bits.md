# 1. 설명
숫자를 이진수로 변경했을때 1의 숫자가 증가하는 방향으로 정렬하세요

1의 숫자가 같은면 원래 10진수가 증가하는 방향으로 정렬하세요.


[문제 링크](https://leetcode.com/problems/sort-integers-by-the-number-of-1-bits/)

어려운 문제는 아니고 

람다, 빌드인 함수 이용해서 얼마나 짧고 효율적으로 작성할 수 있는지 보는 문제

# 2. 코드
### 1) python
```python
class Solution:
    def sortByBits(self, arr: List[int]) -> List[int]:
        return sorted(arr, key=lambda x: (bin(x).count('1'), x))
```

### 2) java
```java
class Solution {
    public int[] sortByBits(int[] arr) {
        return Arrays.stream(arr)
                .boxed()
                .sorted((a, b) -> {
                    int aOneCnt = Integer.bitCount(a);
                    int bOneCnt = Integer.bitCount(b);
                    return aOneCnt == bOneCnt ? a - b : aOneCnt - bOneCnt;
                })
                .mapToInt(i -> i)
                .toArray();
    }
}
```