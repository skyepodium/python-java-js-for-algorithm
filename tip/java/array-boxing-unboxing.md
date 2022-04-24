# 배열 boxing, unboxing

# 1. boxing
boxing할때 `toArray(Integer[]::new)` 넣는 것 자꾸 잊어버린다. 주의하자

```java
class Main {
    public static void main(String args[]) {
        int[] a = {0, 1, 2, 3, 4};

        Integer[] b = Arrays.stream(a).boxed().toArray(Integer[]::new);
    }
}
```

# 2. unboxing
```java
class Main {
    public static void main(String args[]) {
        Integer[] b = {0, 1, 2, 3, 4};

        int[] a = Arrays.stream(b).mapToInt(Integer::intValue).toArray();
    }
}
```