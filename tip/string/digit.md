# 문자열이 숫자인지 판별
# 1. Python
```python
s = "0123456789"
# isdigit, isnumeric의 차이는
# 3², ½와 같은 것을 판별하는데 있다.
# 알고리즘에서는 만날일이 거의 없기 때문에 패스하자

res = s.isdigit()
print('res', res) # True

res = s.isnumeric()
print('res', res) # True
```
# 2. Java
Character 클래스의 isDigit 메서드를 사용한다.

Integer.pareseInt 등의 메소드를 try, catch와 함께 사용할 수도 있지만 다음과 같은 이슈가 있다.
- 0부터 시작하는 경우
- 숫자 자료형 범위를 넘어가는 경우
```java
class Main {
    public static void main(String[] args) {
        String s = "0123456789";
        boolean res = isDigit(s);
        
        System.out.println(res);
    }
    public static boolean isDigit(String s) {
        int size = s.length();
        for(int i=0; i<size; i++) {
            if(!Character.isDigit(s.charAt(i))) return false;
        }
        return true;
    }
}
```

# 3. JavaScript
```js
const s = "0123456789"

const res = /[0-9]/.test(s)

console.log(res) // true
```