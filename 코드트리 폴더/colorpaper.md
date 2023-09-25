## colorpaper

```java
import java.util.Scanner;
public class Main{
    public static void main(String[] args){

    Scanner sc = new Scanner(System.in);

    int num = sc.nextInt();

    int[][] plane = new int[101][101];
    int[] count = new int[101];

    for (int i = 0; i < num; i++) {

      int a = sc.nextInt();
      int b = sc.nextInt();
      int c = sc.nextInt();
      int d = sc.nextInt();

      // a: 가로, b: 세로, c:가로길이, d: 세로길이

      for (int j = b; j < b + d; j++) {
        for (int k = a; k < a + c; k++) {
          plane[j][k] = i + 1;
        }
      }
    }

    for (int i = 0; i <= 100; i++) {
      for (int j = 0; j <= 100; j++) {
        count[plane[i][j]]++;
      }
    }

    for (int i = 1; i <= num; i++) {
      System.out.println(count[i]);
    }

  }
}
```