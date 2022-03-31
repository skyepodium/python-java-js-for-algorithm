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
import java.util.Arrays;

class Main {
    public static void main(String[] args) {
        int[] arr = {6, 5, 4, 3, 2, 1, 0};

        bubbleSort(arr);

        Arrays.stream(arr).forEach(System.out::println);
    }
    public static void bubbleSort(int[] arr) {

        for(int i=arr.length - 1; i>=0; i--) {
            for(int j=0; j<i; j++) {
                if(arr[j] > arr[j+1]) {
                    int temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
    }
}
```

### 3) JavaScript
```js
const bubbleSort = (arr) => {
    for(let i=arr.length - 1; i>=0; i--) {
        for(let j=0; j<i; j++) {
            if(arr[j] > arr[j+1]) {
                const temp = arr[j]
                arr[j] = arr[j+1]
                arr[j+1] = temp
            }
        }
    }
}
```