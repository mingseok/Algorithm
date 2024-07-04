## Find Winner on a Tic Tac Toe Game

```java
class Solution {
    public String tictactoe(int[][] moves) {
        boolean[][] gridChk = new boolean[3][3];
        String[][] grid = new String[3][3];
        for (int a = 0; a < moves.length; a++) {
            gridChk[moves[a][0]][moves[a][1]] = true;
            if (a % 2 == 0) { //A's turn
                grid[moves[a][0]][moves[a][1]] = "X";
            } else { //B's turn
                grid[moves[a][0]][moves[a][1]] = "O";
            }

        }
        if (chkRow(grid) != null) {
            return chkRow(grid);
        } else if (chkColumn(grid) != null) {
            return chkColumn(grid);
        } else if (chkDiagonal(grid) != null) {
            return chkDiagonal(grid);
        } else {
            for (int p = 0; p < grid.length; p++) {
                for (int q = 0; q < grid.length; q++) {
                    if (!gridChk[p][q]) {
                        return "Pending";
                    }
                }
            }
            return "Draw";
        }
    }

    private static String chkDiagonal(String[][] grid) {
        if (grid[0][0] != null && grid[1][1] != null && grid[2][2] != null) {
            if ((grid[0][0].equals(grid[1][1])) && (grid[0][0].equals(grid[2][2]))) {
                if (grid[0][0].equals("X")) {
                    return "A";
                } else {
                    return "B";
                }
            }
        }

        if (grid[2][0] != null && grid[1][1] != null && grid[0][2] != null) {
            if ((grid[2][0].equals(grid[1][1])) && (grid[2][0].equals(grid[0][2]))) {
                if (grid[2][0].equals("X")) {
                    return "A";
                } else {
                    return "B";
                }
            }
        }
        return null;
    }

    private static String chkColumn(String[][] grid) {
        for (int i = 0; i < grid.length; i++) {
            if (grid[0][i] != null && grid[1][i] != null && grid[2][i] != null) {
                if ((grid[0][i].equals(grid[1][i])) && (grid[0][i].equals(grid[2][i]))) {
                    if (grid[0][i].equals("X")) {
                        return "A";
                    } else if (grid[0][i].equals("O")) {
                        return "B";
                    }
                }
            }
        }
        return null;
    }

    public static String chkRow(String[][] grid) {
        for (int i = 0; i < grid.length; i++) {
            if (grid[i][0] != null && grid[i][1] != null && grid[i][2] != null) {
                if ((grid[i][0].equals(grid[i][1])) && (grid[i][0].equals(grid[i][2]))) {
                    if (grid[i][0].equals("X")) {
                        return "A";
                    } else if (grid[i][0].equals("O")) {
                        return "B";
                    }
                }
            }
        }

        return null;
    }
}
```

<br/><br/>

```java
import javax.swing.JOptionPane;
 
public class TicTacToeTester
{
   public static void main (String [] args)
    {
       char player = 'x';
        TicTacToe game = new TicTacToe();
        while (true)
        {
           System.out.println (game);
            String input = JOptionPane.showInputDialog ("Row for " +
                           player + " (from 0-2 and press Cancel to exit)");
            if (input == null) System.exit(0);
             
            int row = Integer.parseInt (input);
            input = JOptionPane.showInputDialog ("Column for " + player +
                                                " from 0-2 and press Cancel to exit)") ;
            int column = Integer.parseInt (input);
            game.set (row, column, player);
            if (player == 'x')
              player = 'o';
            else
              player = 'x';
        } // while
    }  // main
} // TicTacToeTester
```
