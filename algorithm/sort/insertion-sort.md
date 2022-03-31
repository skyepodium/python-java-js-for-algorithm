#  삽입정렬

# 1. 내용
### 1) 시간복잡도
최선 - O(n)
평균 - O(n^2)    
최악 - O(n^2)

### 2) 특징
참조 지역성이 높아 팀 소트에 사용

# 2. 코드
### 1) Python
```python
def insertion_sort(arr):
    for end in range(1, len(arr)):
        for i in range(end, 0, -1):
            if arr[i-1] > arr[i]:
                arr[i-1], arr[i] = arr[i], arr[i-1]
```

### 2) Java
```java
public void insertionSort(int[] arr) {
    for(int end=1; end<arr.length; end++) {
        for(int i=end; i>0; i--) {
            if(arr[i-1] > arr[i]) {
                int temp = arr[i];
                arr[i] = arr[i-1];
                arr[i-1] = temp;
            }
        }
    }
}
```

### 3) JavaScript
```js
const insertionSort = (arr) => {
    for(let end=1; end<arr.length; end++) {
        for(let i=end; i>0; i--) {
            if(arr[i-1] > arr[i]) {
                const temp = arr[i]
                arr[i] = arr[i-1]
                arr[i-1] = temp
            }
        }
    }
}
```