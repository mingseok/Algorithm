## Number of Islands

```java
class Solution {
    public int numIslands(char[][] grid) {
        int n = grid.length;
        int m = grid[0].length;
        
        int ans = 0;
        for (int i=0; i < grid.length; i++) {
            for (int j=0; j < grid[0].length; j++) {
                if (grid[i][j] == '1') {
                    dfs(i, j, grid);
                    ans++;
                }
            }
        }
        return ans;
    }
    
    public void dfs(int i, int j, char[][] grid) {
        if (i < 0 || i >= grid.length || j < 0 || j >= grid[0].length) return;
        
        if (grid[i][j] == '1') {
            grid[i][j] = '0';
            dfs(i+1, j, grid);
            dfs(i-1, j, grid);
            dfs(i, j+1, grid);
            dfs(i, j-1, grid);
        }
    }
}
```

<br/><br/>

```java
class Solution {
    int dx[] = {0,0,1,-1};
    int dy[] = {1,-1,0,0};

    public int numIslands(char[][] grid) {
        int ans = 0;
        int m = grid.length; 
        int n = grid[0].length;
        Queue<int[]> Q= new LinkedList<>();

        for(int i =0 ;i< m ;i++){
            for(int j =0 ; j< n ;j++){
                if(grid[i][j] == '1'){
                    ans++;
                    Q.offer(new int[]{i,j});
                    grid[i][j] = '2';

                    while(!Q.isEmpty()){
                        int c[] = Q.poll();

                        for(int k = 0 ;k < 4 ;k++){
                            int nx = c[0]+dx[k];
                            int ny = c[1]+dy[k];
                            if(nx < 0 || ny < 0 || nx >m-1 || ny  > n-1 || grid[nx][ny] != '1')continue;
                            Q.offer(new int[]{nx,ny});
                            grid[nx][ny] = '2';
                        }
                    }
                }
            }
        }
        return ans;
    }
}
```
