# 문자열 합성

`+` 연산자를 사용해서 문자열을 합성하지 않고 효율적으로 합성합니다.

# 1. Python
f스트링 사용
```py
name = "Lion"
age = 10

s = f"Hi My name is {name}, {age} years old"

print(s) # Hi My name is Lion, 10 years old
```

# 2. Java
string format은 정규표현식을 동적으로 만들때 유용합니다.

### 1) StringBuilder
```java
public class Main {
    public static void main(String[] args) {
        String name = "Lion";
        int age = 10;

        String s = new StringBuilder("Hi My name is ")
                        .append(name)
                        .append(", ")
                        .append(age)
                        .append(" years old")
                        .toString();

        System.out.println(s);
        // Hi My name is Lion, 10 years old
    }
}
```

### 2) String format
```java
public class Main {
    public static void main(String[] args) {
        String name = "Lion";
        int age = 10;

        String s = String.format("Hi My name is %s, %d years old", name, age);

        System.out.println(s); 
        // Hi My name is Lion, 10 years old
    }
}
```

# 3. JavaScript
템플릿 리터럴 사용
```js
const name = "Lion"
const age = 10

const s = `Hi My name is ${name}, ${age} years old`

console.log(s)
```