#  버블 소트

# 1. 내용
### 1) 복잡도
최선 - O(n)
평균 - O(n^2)    
최악 - O(n^2)
공간복잡도 - O(1)

### 2) 특징
매 단계에서 가장 작은 원소를 해당 인덱스에 삽입

# 2. 코드
### 1) Python
```python
def selection_sort(arr):

    for i in range(len(arr) - 1):
        for j in range(i, len(arr)):
            if arr[i] > arr[j]:
                arr[i], arr[j] = arr[j], arr[i]
                
    return arr
```

### 2) Java
```java
public int[] selectSort(int[] arr) {

    for(int i=0; i<arr.length-1; i++) {
        for(int j=i; j<arr.length; j++) {
            if(arr[i] > arr[j]) {
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }

    return arr;
}
```

### 3) JavaScript
```js
const selectionSort = (arr) => {
    for(let i=0; i<arr.length-1; i++) {
        for(let j=i; j<arr.length; j++) {
            if(arr[i] > arr[j]) {
                let temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }

    return arr;
}
```