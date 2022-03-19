# 문자열 합성

# 1. Python
fString을 사용한다.
```python
name = "rabbit"

age = 3

s = f"Hi My name is {name} and {age} age"

print(s) 
# Hi My name is rabbit and 3 age
```

# 2. Java
- `string +` - 단건, 간단하게 할때 사용
- `StringBuilder ` - 다건 및 스레드 언세이프 환경
- `StringBuffer` - 다건 및 스레드 세이프 환경

```java
class Main {
    public static void main(String[] args) {
        // 1. init
        String name = "rabbit";
        int age = 3;
        
        // 2. string
        String s = "Hi My name is " + name + " and " + age + " age";
        System.out.println(s);
        // Hi My name is rabbit and 3 age

        // 3. StrinBuilder
        StringBuilder sb = new StringBuilder("Hi My name is ");
        sb.append(name);
        sb.append(" and ");
        sb.append(age);
        sb.append(" age");
        System.out.println(sb);
        // Hi My name is rabbit and 3 age
    }
}
```

# 3. JavaScript
템플릿 리터럴을 사용합니다.
```js
const name = "rabbit"

const age = 3

const s = `Hi My name is ${name} and ${age} age`

console.log(s)
// Hi My name is rabbit and 3 age
``` 