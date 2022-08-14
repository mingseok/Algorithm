## division

```java
import java.util.Scanner;

public class aaa {

  static int[] result = new int[30];
  static int cnt;
  static int n;

  public static void getResult(int mySum, int index) {
    if (mySum == n) {
      System.out.print(result[0]);

      for (int i = 1; i < index; i++) {
        System.out.print("+" + result[i]);
      }

      System.out.println();
      cnt++;

    } else {
      int myNumber;

      if (index == 0) {
        myNumber = n - 1;
      } else {
        myNumber = n - mySum; // 1 + 1 + 1 만들때 1 - 1 하면 0이 되기 때문이다.
      }

      for (int i = myNumber; i >= 1; i--) {
        result[index] = i;

        if (index > 0 && result[index - 1] < result[index]) {
          continue;
        }

        getResult(mySum + i, index + 1);
      }
    }
  }

  public static void main(String[] args) {

    Scanner sc = new Scanner(System.in);
    n = sc.nextInt();
    getResult(0, 0);
    System.out.print(cnt);

  }
}
```