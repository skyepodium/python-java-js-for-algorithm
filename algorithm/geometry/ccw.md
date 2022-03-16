[백준 11758 CCW](https://www.acmicpc.net/problem/11758) - CCW

# 1. 참고
[블로그](https://velog.io/@skyepodium/%EA%B8%B0%ED%95%98-CCW-tojy2dp4z8)에 자세히 정리했습니다.

# 1. python
```python
# 1. init
points = []
res = 0
class Point:
    def __init__(self, x, y):
        self.x, self.y = x, y

# 2. input
# 3개의 점을 순서대로 리스트에 입력받습니다.
for _ in range(3):
    a, b = map(int, input().split())
    points.append(Point(a, b))

# 3. ccw
# 세점의 좌표정보를 순서대로 받습니다.
def ccw(r, p, q):
    # 벡터의 외적을 수행합니다.
    # 점 p, q에대해 점 r의 x, y를 빼줘서 그래프를 원점에 맞춥니다.
    first = (p.x - r.x) * (q.y - r.y)
    second = (p.y - r.y) * (q.x - r.x)
    result = first - second

    # 1) 1 이면 벡터rp 기준 점 q는 왼쪽에 존재합니다.
    if result > 0: return 1
    # 2) 0 이면 일직선에 존재
    elif result == 0: return 0
    # 3) -1 이면 벡터rp 기준 점 q는 오른쪽에 존재합니다.
    else: return -1

print(ccw(points[0], points[1], points[2]))
```

# 2. java
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

class Main {
    public static long x, y;
    public static Point[] points = new Point[3];
    public static void main(String[] args) throws IOException {
        // 1. setting
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st;

        // 2. input
        for(int i=0; i<3; i++) {
            st = new StringTokenizer(br.readLine());
            x = Long.parseLong(st.nextToken());
            y = Long.parseLong(st.nextToken());
            points[i] = new Point(x, y);
        }

        System.out.println(ccw(points[0], points[1], points[2]));
    }

    public static int ccw(Point p, Point q, Point r) {
        // 벡터의 외적을 수행합니다.
        // 점 p, q에대해 점 r의 x, y를 빼줘서 그래프를 원점에 맞춥니다.
        long first = (p.x - r.x) * (q.y - r.y);
        long second = (p.y - r.y) * (q.x - r.x);
        long result = first - second;

        // 1) 1 이면 벡터rp 기준 점 q는 왼쪽에 존재합니다.
        if(result > 0) return 1;
        // 2) 0 이면 일직선에 존재
        else if(result == 0) return 0;
        // 3) -1 이면 벡터rp 기준 점 q는 오른쪽에 존재합니다.
        else return -1;
    }
}

class Point {
    long x, y;
    public Point(long x, long y) {
        this.x = x;
        this.y = y;
    }
}
```