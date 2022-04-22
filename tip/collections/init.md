# 컬렉션 초기화

# 내용
컬렉션 프레임워크 list, set을 초기화

한번만 해보면, 잊어버리지 않습니다.


# 코드
### 1. Python
생성자에 리스트를 넣어줍니다.
```python
a = [0, 1, 2, 3, 4]

s = set(a)
```

### 2. Java
배열은 스트림을 통해 리스트 또는 셋으로 변경해줍니다.

primitive 타입은 박싱을 해줍니다.

다만, 스트림의 `Collectors`을 사용했을 때 `HashSet`, `ArrayList`가 반환됩니다.

만약 다른 구현체가 필요하다면 다른 방법을 사용해야합니다.
```java
class Main {
    public static void main(String[] args) {

        int[] a = {0, 1, 2, 3};

        Set<Integer> s = Arrays.stream(a).boxed().collect(Collectors.toSet());

        List<Integer> l = Arrays.stream(a).boxed().collect(Collectors.toList());
    }
}
```

### 3. JavaScript
생성자에 Array를 넣어줍니다.
```js
const a = [1, 2, 3, 4]

const s = new Set(a)
```