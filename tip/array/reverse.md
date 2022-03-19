배열 뒤집기
### 1) python
- 슬라이싱 - 값 반환, 공간복잡도 O(n)
- reverse() - 내부 변경, 공간복잡도 O(1)
```python
s = [1, 2, 3]

# 슬라이싱
s[::-1]

# 내부 변경
s.reverse()
```
### 2) java
투 포인터, 스왑
```java
int[] s = {1, 2, 3};
// 투포인터
int l = 0;
int r = s.length - 1;

while(l < r) {
    // 스왑
    int temp = s[l];
    s[l] = s[r];
    s[r] = temp;
    l++;
    r--;
}
```