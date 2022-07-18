## b부터 a까지 감소

a, b 두 자연수를 입력받아 b부터 a까지 1씩 감소하며 그 값을 출력하는 프로그램을 작성해보세요.

<br/>

## 입력

2 5

<br/>

## 출력

5 4 3 2

<br/>

## 코드

### i >= a; 하지 않고, b >= a; 로 한다면 시간 초과가 발생한다. 

즉, b로 한다면 숫자가 줄어들지 않는다.

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int a = sc.nextInt();
        int b = sc.nextInt();

        for(int i = b; i >= a; i--) {
            
            System.out.print(i + " ");
        }

    }
}
```

<br/><br/>

>**Reference** 
> <br/>
코드트리 : https://www.codetree.ai/missions