## tobin

```java
import java.util.Scanner;

public class Main {

  static int N; 
  static int K;
  public static int[] result = new int[30];

  public static void getResult(int n, int k, int index) {
    
    if (index >= N) {
      for (int i = 0; i < index; i++) {
        System.out.print(result[i]);
      }

      System.out.println();
      return;

    } else { 
      if (k > 0) {
        result[index] = 1;
        getResult(n - 1, k - 1, index + 1);
      }

      if (n - k > 0) { 
        result[index] = 0;
        getResult(n - 1, k, index + 1);
      }
    }
  }

  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    N = sc.nextInt();
    K = sc.nextInt();
    getResult(N, K, 0);
    
  }
  
}
```