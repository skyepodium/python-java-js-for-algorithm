# 1. 설명
- k진수에서 소수의 개수를 구하세요


[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/92335)

# 2. 코드
### 1) Python
```python
import re

def solution(n, k):
    # 1. init
    res = 0

    # 2. int_to_base
    def int_to_base(n, k):
        r = ""
        while n > 0:
            r += str(n % k)
            n //= k
        return r[::-1]

    # 3. int_to_base
    def is_prime(val):
        if val < 2: return False

        for i in range(2, int(val ** 0.5) + 1):
            if val % i == 0: return False
        return True

    num = int_to_base(n, k)

    # 4. check
    ### 1) not zero
    if num.count("0") == 0 and is_prime(int(num)):
        res += 1

    ### 2) regex_list
    regex_list = ["^([1-9]+)0", "0([1-9]+)$", "(?=0([1-9]+)0)"]

    for regex in regex_list:
        for c in re.findall(regex, num):
            if is_prime(int(c)):
                res += 1

    return res
```

### 2) Java
```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

class Solution {
    public int solution(int n, int k) {
        // 1. init
        int res = 0;

        String num = intToBase(n, k);

        if(num.equals(num.replaceAll("0", "")) && isPrime(Long.parseLong(num))) res++;

        String[] regex_list = {"^([1-9]+)0", "0([1-9]+)$", "(?=0([1-9]+)0)"};

        for(String regex: regex_list) {
            Pattern pattern = Pattern.compile(regex);
            Matcher matcher = pattern.matcher(num);
            while(matcher.find()) {
                if(isPrime(Long.parseLong(matcher.group(1)))) res++;
            }
        }

        return res;
    }

    public String intToBase(int n, int k) {
        StringBuilder r = new StringBuilder();

        while(n > 0) {
            r.append(n % k);
            n /= k;
        }

        return r.reverse().toString();
    }

    public boolean isPrime(long val) {
        if(val < 2) return false;

        int mid = (int) Math.sqrt(val);

        for(int i=2; i<=mid; i++) {
            if(val % i == 0) return false;
        }

        return true;
    }
}
```

### 3) JavaScript
```js
const solution = (n, k) => {
    // 1. init
    let res = 0

    // 2. intToBase
    const intToBase = (n, k) => {
        let r = ""
        while(n > 0) {
            r += String(n % k)
            n = ~~(n/k)
        }
        return r.split("").reverse().join("")
    }

    // 3. isPrime
    const isPrime = val => {
        if (val < 2) return false

        for(let i=2; i*i<=val; i++) if(val % i === 0) return false

        return true
    }

    const num = intToBase(n, k)

    // 4. check
    // 1) not zero
    if(num.replace(/0/g, '') === num && isPrime(Number(num))) res++

    // 2) regex_list
    const regex_list = [/^([1-9]+)0/g, /0([1-9]+)$/g, /(?=0([1-9]+)0)/g]

    for(const re of regex_list) {
        const b = [...num.matchAll(new RegExp(re, 'g'))]

        b.forEach(x => {
            if(isPrime(Number(x[1]))) res++
        })
    }

    return res
}
```
