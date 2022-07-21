## 3n + 1 수열

자연수 n이 주어집니다. n에서 시작하여 n이 짝수면 2로 나누고, n이 홀수면 3을 곱하고 1을 더하는 것을 n이 1이 되기 전까지 계속 반복하려고 합니다. 총 몇 번을 반복해야 1이 되는지를 계산하는 프로그램을 작성해보세요.

예를 들어 n = 3인 경우 3 -> 10 -> 5 -> 16 -> 8 -> 4 -> 2 -> 1 순서로 1이 되므로 답이 7이 됩니다.

<br/>

## 입력1 

3

<br/>

## 출력1

7

<br/>

## 입력2

1

<br/>

## 출력2

0

<br/>

## 코드

### 못풀었던 이유는 for문으로 했다가 산으로 갔기 때문이다.

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int a = sc.nextInt();
        int count = 0;

        while(true) {
            
            if(a % 2 == 0) {
                a = a / 2;
                count++;

            } else if(a == 1) {
                System.out.print(count); 
                // 0을 하지 않아도 되는 이유는 어차피 카운터 되지 않으면 0 출력 되기 때문이다.
                break;
                
            } else {
                a = (a * 3) + 1;
                count++;
            }
        }
    }
}
```


<br/><br/>

>**Reference** 
> <br/>
코드트리 : https://www.codetree.ai/missions