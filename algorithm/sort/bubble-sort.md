#  버블 소트

# 1. 내용
### 1) 시간복잡도
최선 - O(nlogn)
평균 - O(nlogn)    
최악 - O(n^2)

### 2) 특징
새로운 메모리 필요없음

# 2. 코드
### 1) Python
```python
def bubble_sort(arr):
    for i in range(len(arr) - 1, 0, -1):
        for j in range(i):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
```

### 2) Java
```java
```

### 3) JavaScript
```js

```