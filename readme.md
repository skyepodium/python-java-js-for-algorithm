# 알고리즘을 위한 파이썬, 자바, 자바스크립트 😃
![cover](./image/banner.png)    


요즘은 코딩테스트를 보면, 언어에 제한을 두는 경우가 있습니다.

- Front - JavaScript
- Machine Learning - python
- Server - Python, Java

`python, Java, JS` 로 문제 풀면서 정리해봅시다.

# 🧩 문제 풀이
파이썬, 자바 2개의 언어로 풀었습니다.

리트코드의 경우 [파이썬 알고리즘 인터뷰](http://www.kyobobook.co.kr/product/detailViewKor.laf?ejkGb=KOR&mallGb=KOR&barcode=9791189909178&orderClick=LEa&Kc=)에 소개된 문제 위주로 진행했습니다.

[리트코드](https://github.com/skyepodium/algorithm-for-python-java/tree/master/examples/leetcode)   

[프로그래머스](https://github.com/skyepodium/algorithm-for-python-java/tree/master/examples/programmers)            
          

# 🧬 알고리즘
## 1. 그래프
### 1) 최단경로
-   [다익스트라](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/graph/shortest-path/dijkstra.md)
    - [백준 1753 : 최단경로](https://www.acmicpc.net/problem/1753)

-   [플로이드](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/graph/shortest-path/floyd.md)
    - [백준 11404 : 플로이드](https://www.acmicpc.net/problem/11404)    

### 2) 완전탐색
-   [DFS, BFS](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/graph/brute-force/dfs-bfs.md)
    - [백준 1260 : DFS와 BFS](https://www.acmicpc.net/problem/1260)

### 3) 최소 스패닝 트리
-   [크루스칼](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/graph/mst/kruskal.md)
    - [백준 1197 : 최소 스패닝 트리](https://www.acmicpc.net/problem/1197)

### 4) 위상정렬
-   [위상정렬](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/graph/dag/topological-sort.md)
    -   [백준 2252: 줄 세우기](https://www.acmicpc.net/problem/2252)
    
## 2. 링크드 리스트
### 1) 러너
-   [러너](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/linked-list/runner.md)
    -   [leetcode: linked-list-cycle](https://leetcode.com/problems/linked-list-cycle/)

### 2) 링크드 리스트 뒤집기
-   [링크드 리스트 뒤집기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/linked-list/reverse.md)
    -   [leetcode: linked-list-cycle](https://leetcode.com/problems/reverse-linked-list/)

# 3. 이진탐색
### 1) 바이너리 서치
-   [바이너리 서치](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/binary-search/binary-search.md)
    -   [leetcode: binary-search](https://leetcode.com/problems/binary-search/)

### 2) lowerbound, upperbound
-   [lowerbound, upperbound](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/binary-search/lowerbound-upperbound.md)
    -   [백준 10816: 숫자 카드 2](https://www.acmicpc.net/problem/10816)
    -   [leetcode - https://leetcode.com/problems/find-target-indices-after-sorting-array/](https://leetcode.com/problems/find-target-indices-after-sorting-array/)

# 4. 수학
### 1) GCD, LCM
-   [GCD](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/math/gcd.md)
    -   [백준 2609: 최대공약수와 최소공배수](https://www.acmicpc.net/problem/2609)

### 2) 에라토스테네스의 체 - 소수판별    
-   [eratos](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/math/eratos.md)
    -   [백준 1929: 소수 구하기](https://www.acmicpc.net/problem/1929)

# 5. 기하
### 1) CCW
-   [CCW](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/geometry/ccw.md)
    -   [백준 11758: CCW](https://www.acmicpc.net/problem/11758)

# 6. 정렬
|알고리즘|최선|평균|최악|stable 여부|비고|
|-------|-------|-------|-------|-------|-------|
|퀵소트|O(nlong)|O(nlong)|O(n^2)|X|추가 메모리 사용 없음|
|버블소트|O(n^2)|O(n^2)|O(n^2)|O|iteration 마다 가장 큰 원소가 제일 뒤로 이동|

### 1) [퀵소트](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/sort/quick-sort.md)       




# 🎃 자료구조
## 1. 해시맵
- [Seperate Chaining](https://github.com/skyepodium/python-java-for-algorithm/blob/master/data-structure/hashmap/seperate-chaining.md)
- [Open Adress](https://github.com/skyepodium/python-java-for-algorithm/blob/master/data-structure/hashmap/open-address.md)
    -   [leetcode - design-hashmap](https://leetcode.com/problems/design-hashmap/)

## 2. 트라이
- [prefix-tree](https://github.com/skyepodium/python-java-js-for-algorithm/blob/master/examples/leetcode/trie/implement-trie-prefix-tree.md)
    - [leetcode - implement-trie-prefix-tree](https://leetcode.com/problems/implement-trie-prefix-tree/)


## 3. 큐, 덱
- [queue-deque](https://github.com/skyepodium/python-java-for-algorithm/blob/master/data-structure/dequeue/deque.md)


# 📕 팁
## 1. 내장함수
[정렬 - 내장함수](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/sort/builtin.md)

[trim - 앞뒤 공백 제거](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/trim.md)



## 2. 문자열
[특정 문자열 제거](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/remove.md)         

[문자열 뒤집기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/reverse.md)     

[문자열을 특정 단어 기준으로 분리해서 리스트로 만들기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/split-base.md)     

[문자열 정렬](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/sort.md)        

[문자열이 숫자인지 판별](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/digit.md)     

[대문자, 소문자로 변경](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/lower-upper.md)

[문자열 배열로 만들기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/string-to-array.md)

[문자열 합성](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/concat.md)

[정규식 - 와일드 카드](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/wildcard.md)

[아스키 코드 값 구하기, 아스키코드에서 문자 구하기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/ascii.md)

[정규표현식으로 특정 문자열 모두 검색](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/regex-search.md)

[전체 문자열이 정규표현식과 맞는지 검사](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/regex-match.md)

## 3. 배열
[배열 뒤집기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/reverse.md)     

[짧은 배열 반환](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/short-return.md)

[2차원 배열 생성](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/2d.md)

[배열 자르기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/array-slice.md)

[배열 문자열로 만들기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/array-to-string.md)

[함수형 프로그래밍은 도중에 중단할 수 없습니다.](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/functional.md)

[배열 0 ~ n-1 까지 초기화하기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/fill.md)

[배열에서 최소값, 최대값 찾기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/min-max.md)
## 4. 수학
[3개의 숫자중에서 최대값 구하기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/math/3max.md)

## 5. 인접리스트
[인접 리스트 만들기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/list/adjacent.md)

## 6. 파이썬
[파이썬 리스트 출력](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/python/python-list-print.md)

[defaultdict](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/python/defaultdict.md)

[Counter](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/python/counter.md)

## 7. 연산자
[정수 나눗셈, 몫 구하기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/operator/division.md)

## 8. 입출력
[입출력](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/io/input-output.md)
