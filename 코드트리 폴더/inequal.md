## inequal

```java
import java.util.Scanner;

public class aaa {

  static int n;
  static int[] result = new int[15]; // 값 출력 용도
  static int[] checkMax = new int[15]; // 해당 숫자 있는지 확인 용도
  static char[] myInput = new char[15];
  static boolean printMax = false;

  static int[] checkMin = new int[15];
  static boolean printMin = false;

  public static void getMax(int x) {
    if (printMax == true) {
      return;
    }

    if (x > n) {
      for (int i = 0; i < n + 1; i++) {
        System.out.print(result[i]);

      }

      System.out.println();
      printMax = true;

    } else {
      for (int i = 9; i >= 0; i--) {
        result[x] = i;

        if (checkMax[i] == 0) {

          boolean flag = false;

          if (x == 0) {
            flag = true;
          }

          else {
            if (myInput[x - 1] == '>') {
              if (result[x - 1] > result[x]) {
                flag = true;
              }

            } else {
              if (result[x - 1] < result[x]) {
                flag = true;
              }

            }
          }

          if (flag == true) {
            checkMax[i] = 1;
            getMax(x + 1);
            checkMax[i] = 0;

          }

        }
      }
    }
  }

  public static void getMin(int x) {
    if (printMin == true) {
      return;
    }

    if (x > n) {
      for (int i = 0; i < n + 1; i++) {
        System.out.print(result[i]);

      }

      System.out.println();
      printMin = true;

    } else {
      for (int i = 0; i <= 9; i++) {
        result[x] = i;

        if (checkMin[i] == 0) {

          boolean flag = false;

          if (x == 0) {
            flag = true;
          }

          else {
            if (myInput[x - 1] == '>') {
              if (result[x - 1] > result[x]) {
                flag = true;
              }

            } else {
              if (result[x - 1] < result[x]) {
                flag = true;
              }

            }
          }

          if (flag == true) {
            checkMin[i] = 1;
            getMin(x + 1);
            checkMin[i] = 0;

          }

        }
      }
    }
  }

  public static void main(String[] args) {

    Scanner sc = new Scanner(System.in);

    n = sc.nextInt();

    for (int i = 0; i < n; i++) {
      myInput[i] = sc.next().charAt(0);
    }
    getMax(0);
    getMin(0);

  }
}
```