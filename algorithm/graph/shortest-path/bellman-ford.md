[백준 11657 타임머신](https://www.acmicpc.net/problem/11657) - 벨만 포드

# 1. Python
```python
import sys
input = sys.stdin.readline
print = sys.stdout.write

max_val = 2147483647
n, m = map(int, input().split())

v = []
dist = [max_val] * (n+1)

for _ in range(m):
    cur, next, cost = map(int, input().split())
    v.append((cur, next, cost))

dist[1] = 0
negative_cycle = False
for i in range(1, n+1):
    for cur, next, cost in v:
        if dist[cur] != max_val and dist[next] > dist[cur] + cost:
            dist[next] = dist[cur] + cost
            if i == n: negative_cycle = True

if negative_cycle:
    print("-1\n")
else:
    for i in range(2, n+1):
        if dist[i] == max_val:
            print("-1\n")
        else:
            print("%d\n" % dist[i])
```