# 계수 정렬

# 1. 내용
### 1) 시간복잡도
최선 - O(n + k)    
평균 - O(n + k)    
최악 - O(n + k)    

### 2) 공간복잡도
O(k)

### 2) 특징
순서가 있는 집합에서 원소의 개수대로 배열 생성


# 2. 코드
### 1) Python
```python
def counting_sort(arr):
    min_val, max_val = min(arr), max(arr)
    base = [0 for _ in range(min_val, max_val + 1)]
    res = []

    for a in arr:
        base[a - min_val] += 1

    for idx, b in enumerate(base):
        for _ in range(b):
            res.append(idx + min_val)


    return res
```

### 2) Java
```java
public int[] countingSort(int[] arr) {
    int maxVal = Arrays.stream(arr).max().getAsInt();
    int minVal = Arrays.stream(arr).min().getAsInt();
    int[] base = new int[maxVal - minVal + 1];
    int[] res = new int[arr.length];
    int resIdx = 0;

    Arrays.stream(arr).forEach(x -> base[x - minVal]++);

    for(int i=0; i<base.length; i++) {
        int b = base[i];
        for(int j=0; j<b; j++) {
            res[resIdx++] = i + minVal;
        }
    }

    return res;
}
```

### 3) JavaScript
```js
const countingSort = (arr) => {
    const minVal = Math.min(...arr)
    const maxVal = Math.max(...arr)
    const res = []
    const base = Array.from(Array(maxVal - minVal + 1)).fill(0)

    arr.forEach(x => base[x - minVal]++)

    base.forEach((b, idx) => {
        while(b--) res.push(idx + minVal)
    })

    return res
}
```
