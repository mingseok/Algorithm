## a의 b승

a, b 두 자연수를 입력받아 a b 값을 출력하는 프로그램을 작성해보세요.

<br/>

## 입력

2 5

<br/>

## 출력:

32

<br/>

## 코드

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        // 2 2 2 2 2 
        
        // 1 * 2 = 2
        // 2 * 2 = 4
        // 4 * 2 = 8
        // 8 * 2 = 16
        // 16 * 2 = 32

        int a = sc.nextInt();
        int b = sc.nextInt();
        int sum = 1;

        for(int i = 1; i <= b; i++) {
            sum = sum * a;
        }

        System.out.print(sum);

    }
}
```


<br/><br/>

>**Reference** 
> <br/>
코드트리 : https://www.codetree.ai/missions