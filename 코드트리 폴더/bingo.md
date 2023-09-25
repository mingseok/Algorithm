## bingo

```java
import java.util.Scanner;

public class aaa {
  public static void main(String[] args) {

    Scanner sc = new Scanner(System.in);

    int[][] arr = new int[5][5];

    for (int i = 0; i < 5; i++) {
      for (int j = 0; j < 5; j++) {
        arr[i][j] = sc.nextInt();
      }
    }

    int order = 0;

		// for문 i, j 를 사용하는 이유는
		// a를 넣기 위해서 이다.
		// 밑에 코드들은 a 하나를 넣고 -> 찾고 -> 빙고 되었는지 확인 까지 하는 것이다.
    for (int i = 0; i < 5; i++) {
      for (int j = 0; j < 5; j++) {
        int a = 0;

        a = sc.nextInt();
        order++;

        /**
         * 1. a의 위치를 찾아야 하고,
         * 2. a를 지워야 하고,
         * 3. 몇 개의 줄이 지금까지 지워졌는지를 파악
         * 4. 3개 이상의 줄이 지워졌다면 끝
         */

        for (int k = 0; k < 5; k++) {
          for (int p = 0; p < 5; p++) {
            if (arr[k][p] == a) {
              // (k, p) 에 a 가 있구나!
              arr[k][p] = -1;
            }
          }
        }

        int cnt = 0;

        for (int k = 0; k < 5; k++) { // 가로 x의 개수 세기
          // k번째 줄에 x의 객수를 세겠다.
          int Xcnt = 0;
          for (int p = 0; p < 5; p++) {
            if (arr[k][p] == -1) {
              Xcnt++;
            }
          }

          if (Xcnt == 5) {
            cnt++;
          }
        }

        for (int k = 0; k < 5; k++) {
          int Xcnt = 0;
          for (int p = 0; p < 5; p++) {
            if (arr[p][k] == -1) {
              Xcnt++;
            }
          }
          if (Xcnt == 5) {
            cnt++;
          }
        }

        if (arr[0][0] == -1 &&
            arr[1][1] == -1 &&
            arr[2][2] == -1 &&
            arr[3][3] == -1 &&
            arr[4][4] == -1) {
          cnt++;
        }

        if (arr[0][4] == -1 &&
            arr[1][3] == -1 &&
            arr[2][2] == -1 &&
            arr[3][1] == -1 &&
            arr[4][0] == -1) {
          cnt++;
        }

        if (cnt >= 3) {
          System.out.println(order);
          return;
        }

      }
    }

  }
}
```