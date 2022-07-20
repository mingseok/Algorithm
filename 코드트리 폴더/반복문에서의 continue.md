## 친근하지 않은 수

1이상 n이하의 정수 중 친근하지 않은 수의 개수를 출력하는 프로그램을 작성해보세요. 친근한 수란 2, 3 또는 5로 나누어 떨어지는 수를 의미합니다.

<br/>

## 입력

10

<br/>

## 출력

2

<br/>

## 예제 설명

1이상 10이하의 친근하지 않은 수는 1, 7 두 개 뿐입니다.

<br/>

## 코드


```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int a = sc.nextInt();
        int num = 0;

        for(int i = 1; i <= a; i++) {

            if(i % 2 == 0 || i % 3 == 0 || i % 5 == 0) {
                continue;
            }

            num++;
        }
        
        System.out.print(num);

    }            
}   
```

<br/><br/>

>**Reference** 
> <br/>
코드트리 : https://www.codetree.ai/missions