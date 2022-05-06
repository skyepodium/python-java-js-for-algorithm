# 아스키 코드 값 구하기, 아스키코드에서 문자 구하기

# 1. Python
```python
num = ord('a')

print('num', num) # num 97

ch = chr(num)

print('ch', ch) # ch a
```

# 2. Java
```java
class Main {
    public static void main(String[] args) {
        int num = (int)'a';

        System.out.println("num " + num ); // num 97

        char ch = (char)num;

        System.out.println("ch " + ch); // ch a
    }
}
```

# 3. JavaScript
```js
const num = 'a'.charCodeAt(0)

console.log('num', num) // num 97

const ch = String.fromCharCode(num)

console.log('ch', ch) // ch a
```