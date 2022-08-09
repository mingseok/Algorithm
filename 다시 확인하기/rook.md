```java
import java.util.Scanner;
public class Main{
    public static void main(String[] args){
      
    Scanner sc = new Scanner(System.in);
    
    int[][] arr = new int[8][8];

    int[] rookY = new int[2];
    int[] rookX = new int[2];

    int rookCnt = 0;

    for (int i = 0; i < 8; i++) {
      
      for (int j = 0; j < 8; j++) {
        arr[i][j] = sc.nextInt();

        if (arr[i][j] == 2) {
          // rookY[0], rookX[0] 는 첫 번째 발견되는 룩의 좌표
          // rookY[1], rookX[1] 는 두 번째 발견되는 룩의 좌표
          rookY[rookCnt] = i;
          rookX[rookCnt] = j;

          rookCnt++;
        }
      }
    }

    boolean flag = false;

    for (int k = 0; k < rookCnt; k++) {

      int ry = rookY[k];
      int rx = rookX[k];

      for (int i = rx + 1; i < 8; i++) {
        if (arr[ry][i] == 1) {
          flag = true;
        } else if (arr[ry][i] == 3) {
          break;
        }
      }

      for (int i = ry - 1; i >= 0; i--) {
        if (arr[i][rx] == 1) {
          flag = true;
        } else if (arr[i][rx] == 3) {
          break;
        }
      }

      for (int i = rx - 1; i >= 0; i--) {
        if (arr[ry][i] == 1) {
          flag = true;
        } else if (arr[ry][i] == 3) {
          break;
        }
      }

      for (int i = ry + 1; i < 8; i++) {
        if (arr[i][rx] == 1) {
          flag = true;
        } else if (arr[i][rx] == 3) {
          break;
        }
      }

    }

    if (flag == true) {
      System.out.println("1");
    } else {
      System.out.println("0");
    }

  }
}
```