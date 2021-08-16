# 1. 설명
- 두개를 더해서 target이 되는 인덱스를 반환하세요

- 배열의 길이 1 <= n <= 10만



[문제 링크](https://leetcode.com/problems/two-sum/)

# 2. 코드
### 1) python
```python
class Solution:
    def twoSum(self, nums: list[int], target: int) -> list[int]:

        # 1. 리스트 컴프리헨션으로 (인덱스, 값) 튜플 리스트 생성
        num_list = [(idx, num) for idx, num in enumerate(nums)]

        # 2. 값 기준 정렬
        num_list.sort(key=lambda x: x[1])

        # 3. 투포인터
        l = 0
        r = len(num_list) - 1

        while l < r:
            sum_val = num_list[l][1] + num_list[r][1]
            # 1) 값이 크면 오른쪽 포인터 왼쪽으로
            if sum_val > target:
                r -= 1
            # 2) 값이 작으면 왼쪽 포인터 오른쪽으로
            elif sum_val < target:
                l += 1
            # 3) 값이 같으면, 인덱스 반환
            else:
                return num_list[l][0], num_list[r][0]
```

### 2) java
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {

        // 1. 인덱스와 값을 저장할 ArrayList 생성
        ArrayList<Info> numList = new ArrayList<>();

        // 2. 인덱스와 값 저장
        for(int i=0; i< nums.length; i++) {
            numList.add(new Info(i, nums[i]));
        }

        // 3. 값 기준 오름차순 정렬
        Collections.sort(numList, (a, b) -> {
            return a.getNum() - b.getNum();
        });

        int[] res = new int[2];

        int l = 0;
        int r = numList.size() - 1;

        // 4. 투포인터 사용
        while(l < r) {
            Info lInfo = numList.get(l);
            Info rInfo = numList.get(r);

            int sumVal = lInfo.getNum() + rInfo.getNum();

            // 1) 합이 target보다 크면 오른쪽 포인터 왼쪽으로
            if(sumVal > target) {
                r--;
            }
            // 2) 합이 target보다 작으면 왼쪽 포인터 오른쪽으로
            else if(sumVal < target) {
                l++;
            }
            // 3) 합이 target과 같으면 인덱스 반환
            else {
                res[0] = lInfo.getIdx();
                res[1] = rInfo.getIdx();
                break;
            }
        }

        return res;
    }
}

class Info {

    private int idx;
    private int num;

    public Info(int idx, int num) {
        this.idx = idx;
        this.num = num;
    }

    public int getIdx() {
        return this.idx;
    }

    public int getNum() {
        return this.num;
    }
}
```