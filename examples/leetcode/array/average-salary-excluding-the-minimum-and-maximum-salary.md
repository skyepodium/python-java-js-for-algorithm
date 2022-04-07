# 1. 설명
- 최대, 최소값을 제외한 평균값을 구하세요


[문제 링크](https://leetcode.com/problems/average-salary-excluding-the-minimum-and-maximum-salary/)

# 2. 코드
### 1) Python
```python
class Solution:
    def average(self, salary: List[int]) -> float:
        return (sum(salary) - max(salary) - min(salary)) / (len(salary) - 2)
```

### 2) Java
```java
class Solution {
    public double average(int[] salary) {
        salary = Arrays.stream(salary).sorted().toArray();
        return (Arrays.stream(salary).mapToDouble(x -> x).reduce(Double::sum).getAsDouble() - salary[0] - salary[salary.length-1]) / (salary.length - 2);
    }
}
```

### 3) JavaScript
```js
const average = (salary) => {
    return (salary.reduce((prev, cur) => prev + cur) - Math.max(...salary) - Math.min(...salary)) / (salary.length - 2)
};
```

### 4) TypeScript
```ts
const average = (salary: number[]): number => {
    return (salary.reduce((prev, cur) => prev + cur) - Math.max(...salary) - Math.min(...salary)) / (salary.length - 2)
};
```
