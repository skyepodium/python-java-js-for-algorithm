# 병합정렬

# 1. 내용
### 1) 시간복잡도
최선 - O(nlogn)  
평균 - O(nlogn)  
최악 - O(nlogn)

# 2. 코드
### 1) Python
```python
def merge_sort(arr):
    if len(arr) < 2: return arr

    mid = len(arr) // 2
    low_arr = merge_sort(arr[:mid])
    high_arr = merge_sort(arr[mid:])

    merge_arr = []
    l = h = 0

    while l < len(low_arr) and h < len(high_arr):
        if low_arr[l] < high_arr[h]:
            merge_arr.append(low_arr[l])
            l += 1
        else:
            merge_arr.append(high_arr[h])
            h += 1

    merge_arr += low_arr[l:]
    merge_arr += high_arr[h:]

    return merge_arr
```

### 2) Java
```java
public int[] mergeSort(int[] arr) {
    if(arr.length < 2) return arr;

    int mid = arr.length / 2;
    int[] lowArr = mergeSort(Arrays.copyOfRange(arr, 0, mid));
    int[] highArr = mergeSort(Arrays.copyOfRange(arr, mid, arr.length));

    int[] mergeArr = new int[arr.length];
    int m = 0, l = 0, h = 0;

    while(l < lowArr.length && h < highArr.length) {
        if(lowArr[l] < highArr[h]) {
            mergeArr[m++] = lowArr[l++];
        }
        else{
            mergeArr[m++] = highArr[h++];
        }
    }

    while (l < lowArr.length) {
        mergeArr[m++] = lowArr[l++];
    }
    while (h < highArr.length) {
        mergeArr[m++] = highArr[h++];
    }

    return mergeArr;
}
```

### 3) JavaScript
```js
const mergeSort = (arr) => {
    if(arr.length < 2) return arr

    const mid = ~~(arr.length / 2)
    const lowArr = mergeSort(arr.slice(0, mid))
    const highArr = mergeSort(arr.slice(mid, arr.length))

    let l = 0, h = 0
    const mergeArr = []

    while(l < lowArr.length && h < highArr.length) {
        if(lowArr[l] < highArr[h]) {
            mergeArr.push(lowArr[l++])
        }
        else {
            mergeArr.push(highArr[h++])
        }
    }

    while(l < lowArr.length) {
        mergeArr.push(lowArr[l++])
    }

    while(h < highArr.length) {
        mergeArr.push(highArr[h++])
    }

    return mergeArr
}
```