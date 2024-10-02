## Nearest Exit from Entrance in Maze

```java
import java.util.LinkedList;
import java.util.Queue;

public class NearestExitFromEntrance {
    
    public int nearestExit(char[][] maze, int[] entrance) {
        int rows = maze.length;
        int cols = maze[0].length;

        // 방향 벡터 (상, 하, 좌, 우)
        int[][] directions = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};
        
        Queue<int[]> queue = new LinkedList<>();
        queue.offer(new int[]{entrance[0], entrance[1]});
        
        maze[entrance[0]][entrance[1]] = '+';
        
        int steps = 0;
        
        while (!queue.isEmpty()) {
            int size = queue.size();
            
            for (int i = 0; i < size; i++) {
                int[] current = queue.poll();
                int x = current[0];
                int y = current[1];
                
                // 출구를 찾았는지 확인 (가장자리에서)
                if ((x != entrance[0] || y != entrance[1]) && (x == 0 || x == rows - 1 || y == 0 || y == cols - 1)) {
                    return steps;
                }
                
                // 4가지 방향으로 이동
                for (int[] direction : directions) {
                    int newX = x + direction[0];
                    int newY = y + direction[1];
                    
                    // 유효한 좌표인지 확인
                    if (newX >= 0 && newX < rows && newY >= 0 && newY < cols && maze[newX][newY] == '.') {
                        queue.offer(new int[]{newX, newY});
                        maze[newX][newY] = '+'; // 방문한 위치 표시
                    }
                }
            }
            steps++;
        }
        
        return -1; // 출구를 찾을 수 없을 경우
    }
    
    public static void main(String[] args) {
        NearestExitFromEntrance solution = new NearestExitFromEntrance();
        char[][] maze = {
            {'+', '+', '.', '+'},
            {'.', '.', '.', '+'},
            {'+', '+', '+', '.'}
        };
        int[] entrance = {1, 2};
        System.out.println(solution.nearestExit(maze, entrance)); // 출력: 1
    }
}

```
