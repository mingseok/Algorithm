## algorithm

[문제해결방법론](https://github.com/mingseok/Algorithm/blob/main/%EB%AC%B8%EC%A0%9C%ED%95%B4%EA%B2%B0%EB%B0%A9%EB%B2%95%EB%A1%A0/%EB%AC%B8%EC%A0%9C%ED%95%B4%EA%B2%B0%EB%B0%A9%EB%B2%95%EB%A1%A0.md)

</br>

### 알고리즘을 풀며, 문제가 되었던 리스트.

- BFS는 시작전에 내 위치를 꼭 찍자

    - EX) : board[1][1] = 1;


- input 입력할때 int[][] 을 다룰때 x, y가 반대로 나오는 경우가 있다.

    - 그런 경우 다시 컬렉션이나, 변수를 사용하여 다시 교체하면 되니 어렵게 생각하지 말자.
    
    ```java
        m = kb.nextInt();
        n = kb.nextInt();
        board = new int[n][m];
        
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                Q.offer(new Point(i, j));
            }
        }
    ```




</br>

### 알고리즘 문제를 푸는 레포지토리.

- 코드트리 : 코드트리 문제를 해결한 소스코드 입니다.

    - [소스 폴더 보기](https://github.com/mingseok/Algorithm/tree/main/%EC%BD%94%EB%93%9C%ED%8A%B8%EB%A6%AC%20%ED%8F%B4%EB%8D%94)

</br>


- 프로그래머스 : 프로그래머스 문제를 해결한 소스코드 입니다.

    - [소스 폴더 보기]()

</br>

- 백준 알고리즘 : 백준 알고리즘 문제를 해결한 소스코드 입니다.

    - 백준 알고리즘 번호에 따라 Main_[번호] 규칙으로 정렬

    - [소스 폴더 보기](https://github.com/mingseok/Algorithm/tree/main/%EB%B0%B1%EC%A4%80%20%ED%8F%B4%EB%8D%94)


</br>


- 리트코드 : 리트코드 문제를 해결한 소스코드 입니다.

    - 백준 알고리즘 번호에 따라 Solution[번호] 규칙으로 정렬

    - [소스 폴더 보기]()


</br>

- 필수 알고리즘.

    - [소스 폴더 보기](https://github.com/mingseok/Algorithm/tree/main/%ED%95%84%EC%88%98%20%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98)

