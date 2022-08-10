## baseball game

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