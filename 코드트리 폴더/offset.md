## offset


```java
import java.util.Scanner;
public class Main{
    public static void main(String[] args){

      Scanner sc = new Scanner(System.in);
      int[][] arr = new int[10][10];
      
      for(int i = 1; i <= 5; i++) {
        for(int j = 1; j <= 5; j++) {
          arr[i][j] = sc.nextInt(); 
        }
      }
      
      for(int i = 0; i < 7; i++) {
        arr[0][i] = 99;
      }
      
      for(int i = 0; i < 7; i++) {
        arr[6][i] = 99;
      }
      
      for(int i = 0; i < 7; i++) {
        arr[i][0] = 99;
      }
      
      for(int i = 0; i < 7; i++) {
        arr[i][6] = 99;
      }
      
      
      
      for(int i = 1; i < 6; i++) {
        for(int j = 1; j < 6; j++) {
          
          if(arr[i-1][j] > arr[i][j] &&
             arr[i][j-1] > arr[i][j] &&
             arr[i][j+1] > arr[i][j] &&
             arr[i+1][j] > arr[i][j]) {
               
               System.out.print("*" + " ");
               
               
             }else {
               System.out.print(arr[i][j] + " ");
             }
          
        }
        System.out.println();
      }
  }
}
```