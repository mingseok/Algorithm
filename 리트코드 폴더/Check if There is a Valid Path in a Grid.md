## Check if There is a Valid Path in a Grid

```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    int[][][] dirs = {
        {{0, -1}, {0, 1}},
        {{-1, 0}, {1, 0}},
        {{0, -1}, {1, 0}},
        {{0, 1}, {1, 0}},
        {{0, -1}, {-1, 0}},
        {{0, 1}, {-1, 0}}
};
    public boolean hasValidPath(int[][] grid) {
        int m=grid.length, n =grid[0].length;
        int[][] visited = new int[m][n];
        Queue<int[]> front = new LinkedList<>();
        front.add(new int[]{0,0});
        visited[0][0] = 1;
        while(!front.isEmpty()){
            int[] pos = front.poll();
            
            int num = grid[pos[0]][pos[1]]-1;
            for(int[] dir:dirs[num]){
                int nr = dir[0]+pos[0], nc=dir[1]+pos[1];
                
                if(nr<0 || nr>=m || nc<0 || nc>=n || visited[nr][nc]==1) continue;
                for(int[] backdir:dirs[grid[nr][nc]-1]){
                    if(nr+backdir[0] == pos[0] && nc+backdir[1]==pos[1]){
                        
                        visited[nr][nc] = 1;
                        front.add(new int[]{nr,nc});
                    }
                }

            }
        }
        return visited[m-1][n-1]==1;
    }
}
```

<br/><br/>


```java
public class Solution {
    public boolean hasValidPath(int[][] grid) {
        int rows = grid.length;
        int cols = grid[0].length;
        boolean[][] visited = new boolean[rows][cols];
        return dfs(grid, 0, 0, visited);
    }
    
    private boolean dfs(int[][] grid, int r, int c, boolean[][] visited) {
        int rows = grid.length;
        int cols = grid[0].length;
        
        if (r == rows - 1 && c == cols - 1) {
            return true;
        }
        
        visited[r][c] = true;
        int type = grid[r][c];
        
        for (int[] dir : DIRECTIONS[type]) {
            int newR = r + dir[0];
            int newC = c + dir[1];
            
            if (newR >= 0 && newR < rows && newC >= 0 && newC < cols && !visited[newR][newC]) {
                int newType = grid[newR][newC];
                
                for (int[] newDir : DIRECTIONS[newType]) {
                    if (newR + newDir[0] == r && newC + newDir[1] == c) {
                        if (dfs(grid, newR, newC, visited)) {
                            return true;
                        }
                        break;
                    }
                }
            }
        }
        visited[r][c] = false;
        return false;
    }
}
```
