
# 1. 설명
- 최대 2명이 탈 수 있다. 최소 보트의 개수를 구하세요


[문제 링크](https://leetcode.com/problems/boats-to-save-people/)

풀이방법은 많다. deque, 투포인터 등

# 2.  코드
### 1) Python
```python
class Solution:
    def numRescueBoats(self, people: List[int], limit: int) -> int:
        # 1. init
        dq = deque(sorted(people, reverse=True))
        res = 0

        # 2. loop
        while dq:
            front = dq.popleft()
            if dq and front + dq[-1] <= limit:
                dq.pop()
            res += 1

        return res
```
### 2) Java
```java
class Solution {
    public int numRescueBoats(int[] people, int limit) {
        // 1. init
        int res = 0;
        int s = 0;
        int e = people.length - 1;

        // 2. sort
        people = IntStream.of(people)
                .boxed()
                .sorted(Comparator.reverseOrder())
                .mapToInt(i -> i)
                .toArray();

        // 3. loop
        while(s <= e) {
            int first = people[s];

            if(s < e && first + people[e] <= limit){
                e--;
            }
            s++;
            res++;
        }

        return res;
    }
}
```

### 3) JavaScript
```js
const numRescueBoats = (people, limit) => {
    // 1. init
    people.sort((a, b) => b-a)
    let res = 0
    let s = 0
    let e = people.length - 1

    // 2. loop
    while(s <= e) {
        const first = people[s]
        if(s < e) {
            const last = people[e]
            if(first + last <= limit) e--
        }
        res++
        s++
    }

    return res
};
```