## attackrange

```java
import java.util.Scanner;

public class aaa {
  public static void main(String[] args) {

    Scanner sc = new Scanner(System.in);
    int num = sc.nextInt();

    int y = sc.nextInt();
    int x = sc.nextInt();
    int c = sc.nextInt();

    int[][] arr = new int[105][105];

    // 굳이 1부터 시작하는 이유는??
    // 문제를 보면 4 5 3 의 4를 따라 내려가보면
    // 첫번째줄이 1이기 때문이다.
    for (int i = 1; i <= num; i++) {
      for (int j = 1; j <= num; j++) {

        int first = i - y;
        int second = j - x;

        if (first < 0) {
          first *= -1;
        }

        if (second < 0) {
          second *= -1;
        }

        int dist = first + second;

        if (dist == 0) { // x 부분
          arr[i][j] = -1;
        } else if (dist <= c) {
          arr[i][j] = dist;

        }
      }
    }

    for (int i = 1; i <= num; i++) {
      for (int j = 1; j <= num; j++) {

        if (arr[i][j] == -1) {
          System.out.print("x ");
        } else {
          System.out.print(arr[i][j] + " ");
        }
      }
      System.out.println();
    }

  }
}
```