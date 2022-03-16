[leetcode - 숫자 카드 2](https://www.acmicpc.net/problem/10816) - lowerbound, upperbound

# 1. 정의
lowerbound - target 이상이 값이 나오는 첫 인덱스
upperbound - target 초과의 값이 나오는 첫 인덱스
# 2. 참고
- right(end) 인덱스는 범위를 벗어난다.
- lower, upper 코드는 같다 다른 부분은 `a[mid] <= target`
- right(end) 인덱스를 반환한다.


# 1. python
## 1) loop
```python
# 1. input
n = int(input())
a = list(map(int, input().split()))
m = int(input())
nums = list(map(int, input().split()))
res = []

# 2. sort
a.sort()

# 3. lower bound
def lower_bound(target):
    s, e = 0, n

    while s < e:
        mid = s + (e-s) // 2
        if a[mid] < target:
            s = mid + 1
        else:
            e = mid

    return e

# 4. upper bound
def upper_bound(target):
    s, e = 0, n

    while s < e:
        mid = s + (e-s) // 2

        if a[mid] <= target:
            s = mid + 1
        else:
            e = mid

    return e

for num in nums:
    res.append(upper_bound(num) - lower_bound(num))

print(*res)
```

# 2. java
```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

class Main {
    public static int n, m, a[], nums[];
    public static void main(String[] args) throws IOException {
        // 1. setting
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st;

        // 2. input
        st = new StringTokenizer(br.readLine());
        n = Integer.parseInt(st.nextToken());
        a = new int[n];
        st = new StringTokenizer(br.readLine());
        for(int i=0; i<n; i++) {
            a[i] = Integer.parseInt(st.nextToken());
        }
        st = new StringTokenizer(br.readLine());
        m = Integer.parseInt(st.nextToken());
        nums = new int[m];
        st = new StringTokenizer(br.readLine());
        for(int i=0; i<m; i++) {
            nums[i] = Integer.parseInt(st.nextToken());
        }

        // 3. sort
        Arrays.sort(a);

        StringBuilder sb = new StringBuilder();

        for(int i=0; i<m; i++) {
            sb.append(upperBound(nums[i]) - lowerBound(nums[i]));
            sb.append(" ");
        }
        System.out.println(sb);
    }

    public static int lowerBound(int target) {
        int s = 0;
        int e = n;

        while(s < e) {
            int mid = s + (e-s) /2;
            if(a[mid] < target) {
                s = mid + 1;
            }
            else {
                e = mid;
            }
        }

        return e;
    }

    public static int upperBound(int target) {
        int s = 0;
        int e = n;

        while(s < e) {
            int mid = s + (e-s) / 2;
            if(a[mid] <= target) {
                s = mid + 1;
            }
            else {
                e = mid;
            }
        }

        return e;
    }
}
```