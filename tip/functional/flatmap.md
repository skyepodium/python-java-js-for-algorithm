# flatmap

# 내용
flatmap은 2차원 이상의 배열 또는 리스트를 평탄화 해주는 메서드입니다.

```python
[[1, 2], [3, 4]]

[1, 2, 3, 4]
```

# 요약
- python - sum, 리스트 컴프리헨션
- java - ...
- JavaScript - flatmap

# flatmap 적용 가능 문제
[shuffle-the-array](https://leetcode.com/problems/shuffle-the-array/)

# 코드
### 1. Python
여러 방법이 있지만, 코딩테스트는 시간을 효율적으로 사용해야하기 때문에 제일 추천하는 방법은 sum을 사용하는 압벙

- sum
```python
a = [[1, 2], [3, 4]]

res = sum(a, [])

print('res', res) # [1, 2, 3, 4]
```

- 리스트 컴프리 헨션
```python
a = [[1, 2], [3, 4]]

res = [y for x in a  for y in x]

print('res', res) # [1, 2, 3, 4]
```

### 2. Java
flatmap을 사용합니다. 내부적으로 `inner stream`을 하나 더 만듭니다.
```java
import java.util.Arrays;

class Main {
    public static void main(String[] args) {

        int[][] a = {{1, 2}, {3, 4}};

        int[] res = Arrays.stream(a)
                        .flatMapToInt(Arrays::stream)
                        .toArray();

        Arrays.stream(res).forEach(System.out::println);
    }
}
```

### 3. JavaScript
flatmap 함수를 사용합니다.
```js
const a = [[1, 2], [3, 4]]

const res = a.flatMap(x => x)

console.log('res', res) // [ 1, 2, 3, 4 ]
```