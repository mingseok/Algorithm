## Unique Paths 2

```java
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m = obstacleGrid.length;
        int n = obstacleGrid[0].length;

        if (obstacleGrid[0][0] == 1) return 0;

        obstacleGrid[0][0] = 1;

        for (int x = 1; x < n; ++x) {
            obstacleGrid[0][x] = (obstacleGrid[0][x] == 0 && obstacleGrid[0][x - 1] == 1) ? 1 : 0;
        }

        for (int y = 1; y < m; ++y) {
            obstacleGrid[y][0] = (obstacleGrid[y][0] == 0 && obstacleGrid[y - 1][0] == 1) ? 1 : 0;
        }

        for (int y = 1; y < m; ++y) {
            for (int x = 1; x < n; ++x) {
                if (obstacleGrid[y][x] == 0) {
                    obstacleGrid[y][x] = obstacleGrid[y - 1][x] + obstacleGrid[y][x - 1];
                } else {
                    obstacleGrid[y][x] = 0;
                }
            }
        }

        return obstacleGrid[m - 1][n - 1];
    }
}
```
