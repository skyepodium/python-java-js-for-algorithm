#  퀵소트

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


arr = [5, 1, 6, 3, 4, 2, 7]

arr = [1, 2, 3, 5, 5, 6, 7]

arr = [9, 8, 7, 6, 5, 4, 3, 2, 1]

quick_sort(arr, 0, len(arr) - 1)

print(arr)
```

### 2) Java
```java
import java.util.Arrays;

class Main {
    public static void main(String[] args) {
        int[] arr = {6, 5, 4, 3, 2, 1, 0};

        quickSort(arr, 0, arr.length - 1);

        Arrays.stream(arr).forEach(System.out::println);
    }

    public static void quickSort(int[] arr, int s, int e) {
        if(s >= e) return;

        int mid = s + (e - s) / 2;
        int pivot = arr[mid];
        int l = s;
        int r = e;

        while(l <= r) {
            while(arr[l] < pivot) l++;
            while(arr[r] > pivot) r--;

            if(l <= r) swap(arr, l, r);
            l++;
            r--;
        }

        quickSort(arr, s, r);
        quickSort(arr, l, e);
    }

    public static void swap(int[] arr, int l, int r) {
        int temp = arr[l];
        arr[l] = arr[r];
        arr[r] = temp;
    }
}
```

### 3) JavaScript
```js
const quickSort = (arr, s, e) => {
    if(s >= e) return

    const swap = (arr, l, r) => {
        let temp = arr[l]
        arr[l] = arr[r]
        arr[r] = temp
    }

    const mid = s + ~~((e - s) / 2)
    const pivot = arr[mid]
    let l = s
    let r = e

    while(l <= r) {
        while(arr[l] < pivot) l++
        while(arr[r] > pivot) r--

        if(l <= r) swap(arr, l, r)
        l++
        r--
    }

    quickSort(arr, s, r)
    quickSort(arr, l, e)
}

arr = [6, 5, 4, 3, 2, 1, 0]

quickSort(arr, 0, arr.length - 1)

arr.forEach(x => console.log(x))
```
