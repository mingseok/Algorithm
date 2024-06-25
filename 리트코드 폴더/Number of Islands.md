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

<br/>
<br/>

```java
class Solution {
    Queue<Point> q = new LinkedList<>();

    public int numIslands(char[][] grid) {
        int answer = 0, r = grid.length, c = grid[0].length;

        for (int i = 0; i < r; i++) {//전체 grid를 돌며
            for (int j = 0; j < c; j++) {
                if (grid[i][j] == '1') {//지상인 경우(+ 방문하지 않은 경우)
                    q.add(new Point(i, j));

                    while (!q.isEmpty()) {//bfs 탐색
                        Point now = q.poll();

                        if (now.r < 0 || now.r >= r || now.c < 0 || now.c >= c
                                 || grid[now.r][now.c] == '0') {//예외 사항
                            continue;
                        }

                        grid[now.r][now.c] = '0';//방문 표시

                        q.add(new Point(now.r + 1, now.c));
                        q.add(new Point(now.r - 1, now.c));
                        q.add(new Point(now.r, now.c + 1));
                        q.add(new Point(now.r, now.c - 1));
                    }

                    ++answer;
                }
            }
        }

        return answer;
    }

    class Point {
        int r, c;

        public Point(int r, int c) {
            this.r = r;
            this.c = c;
        }
    }
}
```
