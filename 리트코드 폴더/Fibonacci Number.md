## Fibonacci Number

```java
    public static int calcRecursiveFibonacci(int n) {
        if (n <= 1) {
            return n;
        } else {
            return calcRecursiveFibonacci(n - 1) + calcRecursiveFibonacci(n - 2);
        }
    }

    public static void main(String[] args) {
        int n = 4;
        System.out.println("계단을 오르는 방식 : " + calcRecursiveFibonacci(n + 1)); // 계단을 오르는 방식 : 5
    }
}
```
