## array 3


## 문제

N이 주어질 때, 다음과 같은 프로그램을 작성해보자.

<br/>

## 입력

첫째 줄에 자연수 N이 주어진다.(1<=N<=100)

<br/>

## 예제 입력

```
3
```

<br/>

## 예제 출력

```
1 2 4
3 5
6
```

<br/>

## 예제 입력

```
5
```

<br/>

## 예제 출력

```
1 2 4 7 11
3 5 8 12
6 9 13
10 14
15
```

<br/>

## 코드

```java
import java.util.Scanner;
public class Main{
    public static void main(String[] args){

    Scanner sc = new Scanner(System.in);

    int A_length = sc.nextInt();
    int B_length = A_length;

    int cnt = 1;
    int current = 1;

    for (int j = 0; j < A_length; j++) {
      int outPut = 0;
      int inner_variable = 0;

      for (int i = 1; i <= B_length; i++) {

        if (i == 1) {
          outPut = current;
          inner_variable = cnt;
        }

        System.out.print(outPut + " ");

        outPut += inner_variable;
        inner_variable++;
      }

      System.out.println();
      B_length--;
      cnt++;
      current += cnt;

    }
  }
}
```