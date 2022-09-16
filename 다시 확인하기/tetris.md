## tetris

```java
import java.util.Scanner;

public class bbb {
	public static void main(String[] args) {

		// 스캐너 사용 선언
		Scanner sc = new Scanner(System.in);
		
		// 가로 크기 선언해주기
		int num_width = sc.nextInt();
		// 세로 크기 선언해주기
		int num_high = sc.nextInt();
		// 배열 크기 선언해주기
		int[][] arr = new int[25][25];

		// 이중 포문으로 (1,1) 부터 ~ (25,25) 까지 돌리면서 
		// arr배열에 차례대로 하나씩 값들을 넣어준다.
		for (int i = 1; i <= num_high; i++) {
			for (int j = 1; j <= num_width; j++) {
				arr[i][j] = sc.nextInt();
			}
		}

		// max 변수는 어느 가로줄에 막대를 넣으면 가장 많이
		// 한줄 빙고가 되는지 최대값을 찾기 위해서이다.
		int max = 0;

		// index변수는 현재 가로줄의 위치를 나타내기 위해서 이다.
		int index = 0;

		// 테트리스 판의 왼쪽부터 오른쪽으로 순서대로 진행하게 포문을 사용한다.
		for (int x = 1; x <= num_width; x++) {

			// yIndex 는 해당 가로번째의 높이가 얼마큼인가를 알기 위한 변수이다
			int yIndex = 0;
			// cnt 는 한줄 빙고 되었을때 카운트 하기 위한 변수이다.
			int cnt = 0;

			// 높이 위치 찾기 위해 포문 돌리기
			for (int y = 1; y <= num_high; y++) {
				if (arr[y][x] == 1) { // 1이 테트리스가 있단 뜻이다.
					yIndex = y; // 여기까지 내려오게 된다면 현재 위치가 테스리스가 있다는 뜻이니 
								// y를 yIndex 변수에 넣어준다.
					break; // 그리고 브레이크
				}
			}

			// yIndex가 나온 것이 0이라면 테트리스가 하나도 없다는 뜻이다.
			if (yIndex == 0) { 
				yIndex = num_high + 1; // 테트리스가 하나도 없기 때문에 num_gigh +1 시켜준다.
				                       // 이유는, 이만큼 포문을 돌리고 그 밑에부터 돌리기 위하여
			}

			// yIndex 가 4 보다 클 경우에만 여기 조건들을 수행하게 되는 것이다.
			// 이유는 4까지 되는 것들이 오게 된다면, 테트리스의 게임 룰이 끝나기 때문에 천장에 닿기 때문
			// 그리고 4는 그 다음 순번때 할게 없기 때문에 4까지 포함 시킨 것이다.
			if (yIndex > 4) {
				
				// 초기값 7부터 ~ 7-4 를 한 만큼 돌리는 것이다.
				// 이유는 어차피 테트리스 막대의 크기는 4이기 때문에 무조건 4를 빼준 것이다.
				for (int y = yIndex - 1; y >= yIndex - 4; y--) {
					arr[y][x] = 1; // 현재 자리에 1를 넣어 줌으로써 테트리가 있다고 표시한다.
				}

				// 테트리스의 빙고를 세는 곳이다.
				// 테스리스의 밑에 줄 부터 빙고가 되었는지 확인하기 위해 초기값을 num_high 로 잡아준것이다.
				// 그리고 맨위인 1이 될때 까지 반복하는 것이다.
				for (int y = num_high; y > 0; y--) {

					// 현재줄에서 빙고가 다 되었는지 확인하는 변수이다.
					int local = 0;

					// y 변수로 해당 칸을 잡아두고, 제일 중요한 가로줄 xx 로 빙고인 즉, 테트리스가 한곳이라도 
					// 빠짐 없이 표시 되어 있나 확인 하는 포문이다.
					for (int xx = 1; xx <= num_width; xx++) {
						if (arr[y][xx] == 1) { 
							local++; // 해당 칸에 표시 되어 있다면 local을 증가 시켜주는 것이다.
						}
					}

					// local 이 테트리스 판의 가로줄과 똑같다면 한줄 빙고라는 뜻이다. 
					if (local >= num_width) {
						cnt++; // 그리하여 cnt를 증가 시켜주는 것이다.
					}
				}

				// 현재 x줄에 빙고가 3개가 나왓다면, 그 다음 줄에서 5개가 되었을 수도 있다 
				// 그리하여 max 변수로 빙고가 많이 나온 줄의 증가값을 저장하는 것이다.
				if (cnt > max) {
					max = cnt;
					index = x; // 제일 빙고가 많이 나온 줄을 저장해 놓는다.
				}

				// 마지막으로 x줄인 2번째를 확인 했다면, 이젠 3번째 줄을 비교해야 된다.
				// 그러기 위해선 2번째로 넣었던 테트리스를 빼야 된다.
				// 그리하여 여기서 7 - 4 를 하여 4개 만큼을 다시 0으로 돌려주는 것이다.
				for (int y = yIndex - 1; y >= yIndex - 4; y--) {
					arr[y][x] = 0;
				}
			}
		}
		// 그리고 출력한다.
		System.out.print(index + " " + max);

	}
}
```