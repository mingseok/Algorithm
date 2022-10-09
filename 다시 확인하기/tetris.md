## tetris

```java
import java.util.Scanner;

public class bbb {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int[][] arr = new int[25][25];
        int width = sc.nextInt();
        int high = sc.nextInt();

        int max = 0;
        int index = 0;

        for (int i = 1; i <= high; i++) {
            for (int j = 1; j <= width; j++) {
                arr[i][j] = sc.nextInt();
            }
        }

        for (int x = 1; x <= width; x++) { // 전체 세로줄

            int Yindex = 0;
            int cnt = 0;

            for (int i = 1; i <= high; i++) { // 높이
                if (arr[i][x] == 1) { // 1이면 스탑
                    Yindex = i;
                    break;
                }
            }

            if (Yindex == 0) {

                // +1 하는 이유는 1,4인 막대를 채울때를 위함이다.
                // 즉, 우리는 배열의 숫자 1이면 스탑을 하여
                // 현재자리가 1이 저장되어 있는 자리에 있는 것이다.
                Yindex = high + 1;
            }

            if (Yindex > 4) {
                // 다시 -1 를 해주는 이유는 현재자리가 1이 저장되어 있는 자리에 있기에
                // 위로 한칸 올려주는 것이다.

                for (int i = Yindex - 1; i >= Yindex - 4; i--) {
                    arr[i][x] = 1;
                }

                for (int i = high; i > 0; i--) {
                    int local = 0;

                    for (int xx = 1; xx <= width; xx++) {
                        if (arr[i][xx] == 1) {
                            local++;
                        }
                    }

                    if (local == width) {
                        cnt++;
                    }
                }

                if (cnt > max) {
                    max = cnt;
                    index = x;
                }

                for (int i = Yindex - 1; i >= Yindex - 4; i--) {
                    arr[i][x] = 0;
                }

            }

        }

        System.out.println(index + " " + max);

    }
}

```