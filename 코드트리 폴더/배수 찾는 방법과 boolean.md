## ab 사이에 있는 c

정수 a, b가 주어지면, a이상 b이하에 c의 배수가 단 하나라도 있는지 판단하는 프로그램을 작성해보세요.

출력 형식
a이상 b이하에 c의 배수가 있다면 YES를, 없다면 NO를 출력해보세요.

<br/>

## 입력1

9 20 7

<br/>

## 출력1

YES

<br/>

## 입력2

53 64 13

<br/>

## 출력2

NO

<br/>

## 코드

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        int a = sc.nextInt();
        int b = sc.nextInt();
        int c = sc.nextInt();

        boolean satisfied = false;

        for(int i = a; i <= b; i++) {

            // a에서 b사이의 값 중 c의 배수가 있는지 확인.
            if(i % c == 0) {
                satisfied = true;
            } 
        }


	    if(satisfied == true) {
            System.out.println("YES");

        } else {
            System.out.println("NO");
        }
    }
}
```

<br/><br/>

>**Reference** 
> <br/>
코드트리 : https://www.codetree.ai/missions