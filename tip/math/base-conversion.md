# 진법 변환

직접 구현해도 괜찮지만, 편하게 하는것이 목적이니까.

단, 자세히 알고 사용하기


# 1. Python
2, 8, 16 진법 변환은 `bin, oct, hex` 함수로 지원하고

나머지는 직접 구현합니다.
```python
d = 10

# 1) 10진수 -> 2, 8, 16 진수 - bin, oct, hex
b = bin(d)
print('b', b) # 0b1010

# 슬라이싱으로 필요없는 문자열을 자를 수 있습니다.
b = bin(d)[2:]
print('b', b) # 1010

#2) n 진수 -> 10진수
d = int(b, 16)
print('d', d) # 10
```

# 2. Java
```java
class Main {
    public static void main(String[] args) {
        int d = 10;

        // 1. 10진수 -> n진수
        String b = Integer.toString(d, 2);
        System.out.println("b " + b); // 1010

        // 2. n진수 -> 10진수
        d = Integer.parseInt(b, 2);
        System.out.println("d " + d); // 10
    }
}
```

# 3. JavaScript
```js
d = 10

// 1.  10진수에서 n진수로 변환
b = d.toString(2)
console.log('b', b) // 101

// 2. n 진수에서 10진수로 변환
d = Number.parseInt(b, 2)
console.log('d', d) // 10
```