## 최대점수 구하기(DFS)

```java
import java.util.*;

class Main {
    static int n, m, answer = 0;
    static int[] score, hours;

    public void DFS(int L, int sum, int timeSum, int[] score, int[] hours) {
        if (timeSum > m) {
            return;
        }

        if (L == n) {
            answer = Math.max(answer, sum);
        } else {
            DFS(L + 1, sum + score[L], timeSum + hours[L], score, hours);
            DFS(L + 1, sum, timeSum, score, hours);
        }
    }
    public static void main(String[] args) {

        /**
         * 총 문제 / 제한시간
         *   점수 / 시간
         */
        Main main = new Main();
        Scanner sc = new Scanner(System.in);

        n = sc.nextInt();
        m = sc.nextInt();

        score = new int[n];
        hours = new int[n];
        for (int i = 0; i < n; i++) {
            score[i] = sc.nextInt();
            hours[i] = sc.nextInt();
        }

        main.DFS(0, 0, 0, score, hours);
        System.out.println(answer);

    }
}
```