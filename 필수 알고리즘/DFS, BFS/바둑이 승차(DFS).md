## 바둑이 승차(DFS)

```java
class Main {
    static int c, n, answer = 0;

    public void DFS(int L, int sum, int[] arr) {
        if (sum > c) {
            return;
        }

        if (L == n) {
            answer = Math.max(answer, sum);
        } else {
            DFS(L + 1, sum + arr[L], arr);
            DFS(L + 1, sum, arr);
        }
    }

    public static void main(String[] args) {
        Main main = new Main();
        Scanner sc = new Scanner(System.in);

        c = sc.nextInt();
        n = sc.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        main.DFS(0, 0, arr);
        System.out.println(answer);
    }
}
```