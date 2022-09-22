## seat

```java
import java.util.Scanner;
public class Main{
    public static void main(String[] args){

       // Please Enter Your Code Here
        final Scanner scan = new Scanner(System.in);
        final int colSize = scan.nextInt();
        final int rowSize = scan.nextInt();
        final int target = scan.nextInt();
        scan.close();

        int ticketing = 0;

        int rowStart = 1;
        int rowEnd = rowSize;

        int colStart = 1;
        int colEnd = colSize;

        while (rowStart <= rowEnd && colStart <= colEnd) {
            // top
            for (int currentRow = rowStart; currentRow <= rowEnd; currentRow++) {
                ticketing++;
                if (ticketing == target) {
                    System.out.println(colStart + " " + currentRow);
                    return;
                }
            }
            colStart++;

            // right
            for (int currentCol = colStart; currentCol <= colEnd; currentCol++) {
                ticketing++;
                if (ticketing == target) {
                    System.out.println(currentCol + " " + rowEnd);
                    return;
                }
            }
            rowEnd--;

            // bottom
            for (int currentRow = rowEnd; currentRow >= rowStart; currentRow--) {
                ticketing++;
                if (ticketing == target) {
                    System.out.println(colEnd + " " + currentRow);
                    return;
                }
            }
            colEnd--;

            // left
            for (int currentCol = colEnd; currentCol >= colStart; currentCol--) {
                ticketing++;
                if (ticketing == target) {
                    System.out.println(currentCol + " " + rowStart);
                    return;
                }
            }
            rowStart++;
        }

        System.out.println(0);
    }
}
```