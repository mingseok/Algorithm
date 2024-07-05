## Shift 2D Grid

```java
class Solution {
    public List<List<Integer>> shiftGrid(int[][] grid, int k) {
        int m = grid.length, n = grid[0].length, mod = m * n;
        k = k % mod;
        Integer[][] newGrid = new Integer[m][n];
        for (int i = 0 ; i < mod; i++) {
            int pre = (i - k + mod) % mod;
            newGrid[i / n][i % n] = grid[pre / n][pre % n];
        }
        
        List<List<Integer>> ans = new ArrayList<>();
        for (int i = 0; i < m; i++) {
            ans.add(Arrays.asList(newGrid[i]));
        }
        return ans;
    }
}
```

<br/>
<br/>

```java
class Solution {
    public int[] findDiagonalOrder(int[][] mat) {
        int row = mat.length;
        int col = mat[0].length;
        int totGrid = row*col;
        
        int sol[] = new int[totGrid];
        
        int curRow = 0, curCol = 0;
        for(int i = 0; i < sol.length; i++){
            sol[i] = mat[curRow][curCol];
            // (curRow+curCol)%2 == 0 Go Up
            if((curRow+curCol)%2 == 0)
            {
                // corner case of last column
                if(curCol == col - 1){
                    curRow++;
                }
                else if(curRow == 0){ // corner case of first row
                    curCol++;
                }
                else { // normal update to go up diagonally
                    curRow--;
                    curCol++;
                }
            } 
            else 
            { // Go Down
                // corner case of last row
                if(curRow == row-1){
                    curCol++;
                }
                else if(curCol == 0){ // corner case of first col
                    curRow++;
                }
                else{ // normal update to go down diagonally
                    curCol--;
                    curRow++;
                }
            }
        }
        
        return sol;
    }
}
```
