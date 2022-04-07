# 배열 boxing, unboxing

# 1. boxing
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