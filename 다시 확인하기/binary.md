## binary

```java
import java.util.Scanner;
public class Main{
    public static void main(String[] args){

      Scanner sc = new Scanner(System.in);
      int[] arr = new int[1005];
      int num = sc.nextInt();
      int j = 0;
      
      for(int i = 0; i < arr.length - 1; i++) {
        if(num % 2 == 1) {
          arr[i] = 1;
          num = num / 2;
        } else if(num % 2 == 0) {
          arr[i] = 0;
          num = num / 2;
        }
      }
      
      for(int i = arr.length - 1; i >= 0; i--) {
        if(arr[i] == 1) {
          j = i;
          break;
        }
      }
      
      for(int i = j; i >= 0; i--) {
        System.out.print(arr[i]);
      }

    }
}
```