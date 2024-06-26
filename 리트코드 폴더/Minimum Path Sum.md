## Minimum Path Sum

```java
class Solution {
    public int minPathSum(int[][] grid) {
        int R = grid.length;
        int C = grid[0].length;
        int[][] memo = new int[R][C];
        
        int ans = findMinPath(grid, 0,0, memo);
        
        return ans;
    }
    
    private static int findMinPath(int[][] grid, int y, int x, int[][] memo){
        if(y >= grid.length || x >= grid[0].length) return Integer.MAX_VALUE;
        if(y == grid.length-1 && x == grid[0].length-1) return grid[y][x];
        
        if(memo[y][x] != 0) return memo[y][x];
        
        int down = findMinPath(grid, y+1,x, memo);
        int right = findMinPath(grid, y,x+1, memo);
        
        memo[y][x] = Math.min(down, right) + grid[y][x];
        
        return memo[y][x];
    }
}
```
