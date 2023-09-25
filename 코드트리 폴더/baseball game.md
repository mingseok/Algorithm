## baseball game


### 기능 목록

- [ ] 부터 9까지의 서로 다른 임의의 수 3개를 생성한다.
- [ ] 컴퓨터의 수(3자리)와 플레이어의 수(3자리)를 비교할 수 있다.
    - [ ] 몇개의 숫자가 같은지를 알수 있어야 한다.
    - [ ] 특정 자리에 특정 숫자가 있는지 알 수 있다.
        - [ ] 같은 수가 같은 자리에 있으면 스트라이크이다.
        - [ ] 같은 수가 다른 자리에 있으면 볼이다.
        - [ ] 같은 수가 전혀 없으면 낫싱이다.


```java
Scanner sc = new Scanner(System.in);
    int[][] arr = new int[105][3];
    int num = sc.nextInt();
    int result = 0;

    for (int i = 0; i < num; i++) {
      arr[i][0] = sc.nextInt();
      arr[i][1] = sc.nextInt();
      arr[i][2] = sc.nextInt();
    }

    for (int i = 1; i <= 9; i++) {
      for (int j = 1; j <= 9; j++) {
        for (int k = 1; k <= 9; k++) {
          // ijk
          if (i != j && j != k && k != i) {
            boolean flag = false;
            for (int p = 0; p < num; p++) {

              int first = arr[p][0] / 100;
              int second = (arr[p][0] / 10) % 10;
              int third = arr[p][0] % 10;

              int strike = 0;
              int ball = 0;

              if (first == i) {
                strike++;
              }

              if (second == j) {
                strike++;
              }

              if (third == k) {
                strike++;
              }

              if (i == second || i == third) {
                ball++;
              }

              if (j == first || j == third) {
                ball++;
              }

              if (k == first || k == second) {
                ball++;
              }

              if (arr[p][1] != strike || arr[p][2] != ball) {
                flag = true;
              }
            }
            
            if (flag == false) {
              result++;
            }
          }
        }
      }
    }
    System.out.print(result);

  }
}
```