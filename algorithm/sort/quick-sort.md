#  퀵소트

# 1. 내용
### 1) 시간복잡도
평균 - O(n)
최악 - O(n^2)

### 2) 특징
새로운 메모리 필요없음

# 2. 코드
### 1) Python
```python
def quick_sort(arr, s, e):
    # 1. excetpion 인덱스 크기 비교 및 종료
    if s >= e: return

    # 2. 피벗과 l, r 인덱스를 설정합니다.
    mid = s + (e - s) // 2
    pivot = arr[mid]
    l, r = s, e

    # 3. 피벗과 l, r 의 값을 비교합니다.
    # l은 클때 까지, r은 작을 때 까지 이동합니다.
    while l <= r:
        while arr[l] < pivot: l += 1
        while arr[r] > pivot: r -= 1

        # 다른 경우가 나오면 swap 합니다.
        if l <= r:
            arr[l], arr[r] = arr[r], arr[l]
            l, r = l + 1, r -1

    # 4. 인덱스 교차후 재귀 호출합니다.
    quick_sort(arr, s, r)
    quick_sort(arr, l, e)
```

### 2) Java
```java

```

### 3) JavaScript
```js

```
