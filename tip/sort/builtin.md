# 정렬 - 내장함수
내장된 정렬 함수를 적용하는 방법에 대해 알아봅시다.

# 참고
### 1) python
파이썬의 내장 정렬 함수는 `팀소트`입니다. `데이터는 이미 대부분 정렬되었다`고 가정합니다.

대부분의 정렬에서 직접 구현보다 `내장함수를 사용하는 것이 빠릅니다`.

단점은 merge sort를 베이스로 하기 때문에 `1/2 n의 공간을 더 사용`합니다.

### 2) java
자바도 `팀소트` 사용합니다.

이펙티브 자바의 저자 조슈아 블로크가 병합정렬을 개선한 방식을 사용했었는데 팀소트가 인기를 끌자 자바 7부터 변경되었습니다.

# 1. 정수 정렬
### 1) python
```python
# 1) sorted - 원본 배열 수정 X - 반환값 정렬된 리스트
l = [1, 2, 3]
print(sorted(l))

# 2) sort - 원본 배열을 변경한다 - 반환값 None
l.sort()
print(l)
```

### 2) java
자바 primitive 타입에 대해서는 역순 정렬을 지원하지 않는다.

[java-sorting-arrays](https://www.baeldung.com/java-sorting-arrays) 에 따르면 
1) 참조타입으로 boxing
2) 역순 정렬
3) 원시타입으로 바꾸는 방법을 사용했습니다.

```java
import java.util.*;
import java.util.stream.IntStream;

class Main {
    public static void main(String[] args) {

        // 1. 배열
        int[] a = {4, 3, 2, 1, 0};
        // 1) 오름 차순
        Arrays.sort(a);

        // 2) 역순 정렬
        IntStream.of(a).boxed().sorted(Comparator.reverseOrder()).mapToInt(i -> i).toArray();

        // 2. 리스트
        List<Integer> l = new ArrayList<>();
        for(int i=4; i>=0; i--) l.add(i);

        // 1) 오름차순
        l.sort(Comparator.naturalOrder());

        // 2) 내림차순
        l.sort(Comparator.reverseOrder());
    }
}
```
### 3) javascript
[MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)에 따르면 내장함수 sort는 문자열의 유니코드 포인트를 따릅니다.

기본 정렬 사용하면 -1.1이 -1 보다 크다고 나옵니다. 
```js
const a = [-1.1, -1, 0]

a.sort() // [-1, -1.1, 0]

a.sort((a, b) => a - b) // [-1.1, -1, 0]
```

람다식을 통해 두 수의 비교를 사용합니다.
반환값이 참이 되도록 진행됩니다.
- 음수 - 오름차순
- 양수 - 오름 차순
```js
const a = [-1.1, -1, 0]

// 오름차순
a.sort((a, b) => a - b)

// 내림차순
a.sort((a, b) => b - a)
```


# 2. 객체 리스트 정렬

자바의 경우 Comparable, Comparator Override 해서 사용할 수는 있는데 코딩 테스트 상황에서 굳이 구현하면 귀찮으니까

가급적 스트립, 람다 사용해서 최대한 단축합니다.

예시) 숫자 오름차순, 문자열 내림차순
### 1) python
```python
l = []
l.append((1, "a"))
l.append((2, "b"))
l.append((2, "c"))

# 문자열에는 -값을 붙일 수 없다.
# 전체에 reverse를 걸고 오름차순 key에 -를 붙인다.
l.sort(key=lambda x: (-x[0], x[1]), reverse=True)

print(l) 
# [(1, 'a'), (2, 'c'), (2, 'b')]
```

### 2) java
```java
import java.util.ArrayList;
import java.util.List;

class Main {
    public static void main(String[] args) {
        List<Info> l = new ArrayList<>();
        l.add(new Info(1, "a"));
        l.add(new Info(2, "b"));
        l.add(new Info(2, "c"));

        // 1) 람다, 2) compareTo 사용
        /*
            compareTo 는 기본적으로 앞의 값 - 뒤의 값으로 구성
            0 보다 작은 경우, a index < b index
            0 과 같은 경우, a index == b index
            0 보다 큰 경우, b index < a index
        */
        l.sort((a, b) -> {
            if(a.num == b.num) return -a.name.compareTo(b.name);
            else return a.num - b.num;
        });

        l.forEach(System.out::println);
    }
}

class Info {
    int num;
    String name;
    public Info(int num, String name) {
        this.num = num;
        this.name = name;
    }
}
```

### 3) javascript
```js
const l = []

l.push([1, "a"])
l.push([2, "b"])
l.push([2, "c"])

l.sort((a, b) => {
    /*
        숫자 비교는 - 사용
        문자 비교는 < === > 검사 후 -1, 0, 1 리턴해도 되는데 코드양이 길어지기 때문에
        localeCompare 적극 사용한다. 
    */
    return a[0] === b[0] ? b[1].localeCompare(a[1]) : a[0] - b[0]
})

console.log('l', l)
```