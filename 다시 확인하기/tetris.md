## tetris

```java
import java.util.Scanner;

public class Main {
  public static void main(String[] args) {

    Scanner sc = new Scanner(System.in);

    int num_width = sc.nextInt();
    int num_high = sc.nextInt();
    int[][] data = new int[25][25];

    for (int i = 1; i <= num_high; i++) {
      for (int j = 1; j <= num_width; j++) {
        data[i][j] = sc.nextInt();
      }
    }

    int max = 0;
    int index = 0;

    for (int x = 1; x <= num_width; x++) {

      int yIndex = 0;
      int cnt = 0;

      for (int y = 1; y <= num_high; y++) {
        if (data[y][x] == 1) {
          yIndex = y;
          break;
        }
      }

      if (yIndex == 0) {
        yIndex = num_high + 1;
      }

      if (yIndex > 4) {

        for (int y = yIndex - 1; y >= yIndex - 4; y--) {
          data[y][x] = 1;
        }

        for (int y = num_high; y > 0; y--) {

          int local = 0;

          for (int xx = 1; xx <= num_width; xx++) {
            if (data[y][xx] == 1) {
              local++;
            }
          }

          if (local >= num_width) {
            cnt++;
          }
        }

        if (cnt > max) {
          max = cnt;
          index = x;
        }

        for (int y = yIndex - 1; y >= yIndex - 4; y--) {
          data[y][x] = 0;
        }

      }

    }
    System.out.print(index + " " + max);

  }
}
```