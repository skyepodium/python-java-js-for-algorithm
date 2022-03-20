# 함수형 프로그래밍은 도중에 중단할 수 없습니다.

# 1. 상황
forEach, map, filter, reduce 등의 메서드들이 있습니다.

람다식 쓰고 편한데 

단점은
1. 중간에 중단할 수 없음
2. return, break 키워드 사용 불가

[프로그래머스 -영어 끝말잇기](https://programmers.co.kr/learn/courses/30/lessons/12981) 같은 문제 반복문 돌다가 중간에 리턴하고 싶은데 반환불가 

반복문 끝가지 순회해야합니다.

# 2. 예시
끝말잇기
- 틀리면 [바로 앞단어, 현재 단어] 반환
- 안틀리면 [-1, -1] 반환

```js
const words = ['apple', 'elepahnt', 'tree', 'fish', 'hat']

// 1. 함수형 프로그래밍
const f = (arr) => {
    let prev = ""
    const res = [-1, -1]
    arr.forEach(w => {
        if(prev !== "" && prev.charAt(prev.length-1) !== w.charAt(0)) {
            if(res[0] === -1 && res[1] === -1) {
                res[0] = prev
                res[1] = w
            }
            // return [prev, w]
            // break 사용불가
        }
        prev = w
    })
    return res
}

// 2. 반복문
const fo = (arr) => {
    let prev = ""
    for(const w of arr) {
        if(prev !== "" && prev.charAt(prev.length-1) !== w.charAt(0)) {
            return [prev, w]
        }
        prev = w
    }
    return [-1, -1]
}

console.log(f(words))
console.log(fo(words))
```

# 3. 정리
- 함수형 메서드 - 전부 순회해야하는 경우 사용
- 반복문 - 중간에 반환해야할 때 사용
