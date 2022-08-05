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

class aaa {
  public static void main(String[] args) {

    Scanner sc = new Scanner(System.in);

    int[][] arr = new int[105][105];
    int n = sc.nextInt();

    int y = 0;
    int x = 0;
    int cnt = 1;

    for (int i = 0; i < n; i++) {
			
			// x, y 변수를 사용하지 않고, 한다면 i, j 가 계속 증가하기 때문이다.
      y = 0; 
      x = i;

      for (int j = 0; j <= i; j++) {
        arr[y][x] = cnt;
        cnt++;

        y++;
        x--;
      }
    }

    for (int i = 0; i < n; i++) {
      for (int j = 0; j < n - i; j++) {
        System.out.print(arr[i][j] + " ");
      }
      System.out.println();
    }

  }
}
```