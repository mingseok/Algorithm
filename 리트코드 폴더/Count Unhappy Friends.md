## Count Unhappy Friends

```java
import java.util.HashMap;
import java.util.Map;

public class CountUnhappyFriends {
    
    public int unhappyFriends(int n, int[][] preferences, int[][] pairs) {
        // 각 친구의 선호도 매트릭스 만들기
        int[][] rank = new int[n][n];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n - 1; j++) {
                rank[i][preferences[i][j]] = j;
            }
        }

        // 친구 쌍을 맵으로 저장
        Map<Integer, Integer> pairMap = new HashMap<>();
        for (int[] pair : pairs) {
            pairMap.put(pair[0], pair[1]);
            pairMap.put(pair[1], pair[0]);
        }

        int unhappyCount = 0;

        // 각 친구 쌍을 순회하면서 불행한 친구 찾기
        for (int x = 0; x < n; x++) {
            int y = pairMap.get(x);
            for (int i = 0; i < rank[x][y]; i++) {
                int u = preferences[x][i];
                int v = pairMap.get(u);
                if (rank[u][x] < rank[u][v]) {
                    unhappyCount++;
                    break;
                }
            }
        }

        return unhappyCount;
    }

    public static void main(String[] args) {
        CountUnhappyFriends solution = new CountUnhappyFriends();
        int n = 4;
        int[][] preferences = {
            {1, 2, 3},
            {3, 2, 0},
            {3, 1, 0},
            {1, 2, 0}
        };
        int[][] pairs = {
            {0, 1},
            {2, 3}
        };
        int result = solution.unhappyFriends(n, preferences, pairs);
        System.out.println(result);  // Expected output: 2
    }
}

```
