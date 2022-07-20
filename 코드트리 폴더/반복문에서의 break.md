## 1부터의 합

정수 n이 주어졌을 때, 1부터 차례대로 100까지 1씩 증가시키며 합을 구하다가 처음으로 그 합이 n 이상이 되는 순간에 더해진 숫자가 무엇인지를 출력하는 프로그램을 작성해보세요.

<br/>


## 출력 형식

첫 번째 줄에는 1부터 증가시키며 더한 값이 n 이상이 되는 순간 더해진 숫자를 출력합니다.

<br/>

## 입력

5

<br/>

## 출력

3

<br/>

## 예제 설명

첫 번째 예제에서는 n이 5라면 1 + 2 + 3이 되는 순간에 5 이상이 되므로 출력값이 3입니다.

<br/>

## 코드

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int a = sc.nextInt();
        int sum = 0;

        for(int i = 1; i <= 100; i++) {

            sum += i;

            if(sum >= a) {
                System.out.print(i);
                break;
            }
        }
    }
}
```

<br/><br/>

다른 문제


## 출력값은 무엇인가?

```java
int x = 100;
for ( x = 1; x <= 5; x++) {  
    if ( x == 2 ) {    
        continue;  
    }  
    if ( x == 4 ) {    
        break;  
    }  
    System.out.print(x + " ");
}
```

답은 1, 3

<br/><br/>

>**Reference** 
> <br/>
코드트리 : https://www.codetree.ai/missions