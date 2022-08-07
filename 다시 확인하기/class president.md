## class president

```java
import java.util.Scanner;

public class aaa {
  public static void main(String[] args) {

    Scanner sc = new Scanner(System.in);
    int num = sc.nextInt();
    int[][] arr = new int[1005][100];

    int result = -1;
    int resultNumber = 0;

    for (int i = 1; i <= num; i++) {
      for (int j = 0; j < 5; j++) {
        arr[i][j] = sc.nextInt();
      }
    }

    for (int i = 1; i <= num; i++) {

      int numStudent = 0; // 나와 곂치는 학생의 수

      for (int j = 1; j <= num; j++) { // 포인트

        if (i == j) {
          continue;
        }

        if (arr[i][0] == arr[j][0] ||
            arr[i][1] == arr[j][1] ||
            arr[i][2] == arr[j][2] ||
            arr[i][3] == arr[j][3] ||
            arr[i][4] == arr[j][4]) {

          numStudent++;
        }
      }

      if (result < numStudent) {
        result = numStudent;
        resultNumber = i; // i는 학생이다.
      }

    }

    System.out.print(resultNumber);
  }
}
```