## Max Area of Island

```java
private final int[][] DIRECTIONS = new int[][]{{-1,0},{0,1},{1,0},{0,-1}};

public int maxAreaOfIsland(int[][] grid) {

    int max = 0;
    boolean[][] isVisited = new boolean[grid.length][grid[0].length];

    for (int i = 0; i < grid.length; i++) {
        for (int j = 0; j < grid[0].length; j++) {
            if(!isVisited[i][j]){
                max = Math.max(max,dfs(grid,isVisited,i,j));
            }
        }
    }
    return max;
    
}

private int dfs(int[][] grid,boolean[][] isVisited, int r, int c){

      if(r < 0 || r >= grid.length || c < 0 || c >=grid[0].length || isVisited[r][c] )return 0;
      isVisited[r][c] = true; //방문 기록
      int area = 0;
      if(grid[r][c] == 1) { //섬이면 주변 섬 스캔  rercusive call
          area++;
          for(int[] d : DIRECTIONS){ // 시계방향 전파
              area += dfs(grid,isVisited,r+d[0],c+d[1]);
          }
      }
      return area;
  }
```
