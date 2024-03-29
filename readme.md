# 알고리즘을 위한 파이썬, 자바, 자바스크립트 😃
![cover](./image/banner.png)    


요즘은 코딩테스트를 보면, 언어에 제한을 두는 경우가 있습니다.

- Front - JavaScript
- Machine Learning - python
- Server - Python, Java

`python, Java, JS` 로 문제 풀면서 정리해봅시다.

# 🧩 문제 풀이
파이썬, 자바, 자바스크립트 3개의 언어로 풀었습니다.

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

-   [벨만포드](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/graph/shortest-path/bellman-ford.md)
    - [백준 11657 : 타임머신](https://www.acmicpc.net/problem/11657)    

- 앙방향 탐색
    - 양방향 BFS

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
    -   [leetcode - find-target-indices-after-sorting-array](https://leetcode.com/problems/find-target-indices-after-sorting-array/)

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
|알고리즘|최선|평균|최악|공간 복잡도|안정|비고|
|-------|-----|-----|-----|-----|-------|-------|
|버블소트|O(n)|O(n^2)|O(n^2)|O(1)|O|iteration 마다 가장 큰 원소가 제일 뒤로 이동|
|삽입정렬|O(n)|O(n^2)|O(n^2)|O(1)|O|참조 지역성 높음|
|선택정렬|O(n)|O(n^2)|O(n^2)|O(1)|X||
|퀵소트|O(nlogn))|O(nlogn)|O(n^2)|O(1)|X|추가 메모리 사용 없음|
|병합정렬|O(nlogn)|O(nlogn)|O(n^2)|O(n)|O|추가 메모리 필요|
|팀소트|O(n)|O(nlogn)|O(nlogn)|O(n)|O|insertion + quick|
|계수정렬|O(n+k)|O(n+k)|O(n+k)|O(k)|X||


### 1) [버블소트](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/sort/bubble-sort.md)      

### 2) [삽입정렬](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/sort/insertion-sort.md)      

### 3) [선택정렬](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/sort/selection-sort.md)   
### 4) [퀵소트](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/sort/quick-sort.md)  

### 5) [병합정렬](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/sort/merge-sort.md)

### 6) [계수정렬](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/sort/counting-sort.md)

# 7. 순열
### 1) 순열
-   [순열](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/permutation/permutation.md)

# 8. 인코딩
### 1) Base64
-   [Base64](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/encoding/Base64.md)

### 2) url 인코딩/decoding
-   [URL](https://github.com/skyepodium/python-java-for-algorithm/blob/master/algorithm/encoding/url.md)


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

## 4. 스택
- [stack](https://github.com/skyepodium/python-java-for-algorithm/blob/master/data-structure/stack/stack.md)

## 5. 그래프
|수행|인접 리스트|인접 행령|인접 셋|
|-------|-----|-----|-----|
|노드 존재 여부 검사|O(m)|O(1)|O(1)|
|순회|O(n)|O(m)|O(v)|O(1)|
|간선 추가|O(1)|O(1)|O(1)|
|간선 제거|O(m)|O(1)|O(1)|

인접셋 문제(https://atcoder.jp/contests/abc278/tasks/abc278_c)


# 🌏 유명한 문제
- N-Queen
    - boj 
        - https://www.acmicpc.net/problem/9663
    - programmers 
        - https://school.programmers.co.kr/learn/courses/30/lessons/12952
    - leetcode
        - https://leetcode.com/problems/n-queens/
        - https://leetcode.com/problems/n-queens-ii/

- triplet - O(N^2)
    - leetcode
        - https://leetcode.com/problems/3sum/
        - https://leetcode.com/problems/increasing-triplet-subsequence/

- LIS(가장 긴 증가하는 부분 수열) - O(NlogN)
    - leetcode
        - https://leetcode.com/problems/longest-increasing-subsequence/

- LCS(가장 긴 공통 부분 수열) - O(nm)
    - boj
        - https://www.acmicpc.net/problem/9251
    - leetcode 
        - https://leetcode.com/problems/longest-common-subsequence

- Knap sack(배낭 문제) - O(nm)
    - boj
        - https://www.acmicpc.net/problem/12865
        - https://www.acmicpc.net/problem/1535

# 📕 팁
## 1. 내장함수
[정렬 - 내장함수](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/sort/builtin.md)

[문자열 배열 정렬](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/sort/string-array-sort.md)

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

[문자열 합성](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/synthesis.md)

[문자열에서 중첩된 부분까지 정규표현식으로 찾기 - 전방탐색](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/lookahead.md)

[숫자, 알파벳 여부 판별](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/check-number-alpha.md)

[연속적인 중복 제거 - stack](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/string/remove-duplicate.md)

## 3. 배열
[배열 뒤집기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/reverse.md)     

[짧은 배열 반환](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/short-return.md)

[다차원 배열 생성](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/nd.md)

[배열 자르기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/array-slice.md)

[배열 문자열로 만들기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/array-to-string.md)

[함수형 프로그래밍은 도중에 중단할 수 없습니다.](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/functional.md)

[배열 0 ~ n-1 까지 초기화하기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/fill.md)

[배열에서 최소값, 최대값 찾기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/min-max.md)

[배열의 합 구하기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/sum.md)

[forEach 인덱스 함께 사용하기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/array/loop-with-index.md)

## 4. 수학
[3개의 숫자중에서 최대값 구하기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/math/3max.md)

[진법 변환](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/math/base-conversion.md)

## 5. 인접리스트
[인접 리스트 만들기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/list/adjacent.md)

## 6. 힙 - 우선순위 큐
[우선순위 큐](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/heap/priority.md)

## 7. 파이썬
[파이썬 리스트 출력](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/python/python-list-print.md)

[defaultdict](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/python/defaultdict.md)

[Counter](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/python/counter.md)

[split - maxsplit](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/python/split-maxsplit.md)

[max, sort key len](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/python/max-key.md)


## 8. 자바
[배열 boxing, unboxing](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/java/array-boxing-unboxing.md)

[배열 -> 리스트, 리스트 -> 배열 변환](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/java/array-list.md)

## 9. 자바스크립트
[자바스크립트 zip - 제너레이터](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/javascript/zip.md)

[정수형 범위 - 예시) 1) shift 연산 vs Math.pow, 2) not not vs Math.trunc](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/javascript/int-range.md)

## 10. 컬렉션
[컬렉션 초기화](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/collections/init.md)

## 11. 함수형 프로그래밍
[flatmap](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/functional/flatmap.md)


## 12. 연산자
[정수 나눗셈, 몫 구하기](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/operator/division.md)

## 13. 입출력
[입출력](https://github.com/skyepodium/python-java-for-algorithm/blob/master/tip/io/input-output.md)
