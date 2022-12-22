Problem - [Sudoku Solver](https://leetcode.com/problems/sudoku-solver/)

- Given a 9×9 incomplete sudoku, solve it such that it becomes valid sudoku. Valid sudoku has the following properties.

         1. All the rows should be filled with numbers(1 – 9) exactly once.

         2. All the columns should be filled with numbers(1 – 9) exactly once.

         3. Each 3×3 submatrix should be filled with numbers(1 – 9) exactly once.

Note: Character ‘.’ indicates empty cell.

- Example

![image](https://user-images.githubusercontent.com/101946115/209066876-833cc34e-603c-4332-a684-d44e547ef2ff.png)

Explanation:

The empty cells are filled with the possible numbers. There can exist many such arrangements of numbers. The above solution is one of them. Let’s see how we can fill the cells below.

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
import java.util.*;

class Solution {
    public static boolean solve(char[][] board) {
    for (int i = 0; i < 9; i++) {
      for (int j = 0; j < 9; j++) {
        if (board[i][j] == '.') {

          for(char c = '1'; c <= '9'; c++) {
            if (isValid(board, i, j, c)) {
              board[i][j] = c;

              if (solve(board))
                return true;
              else
                board[i][j] = '.';
            }
          }

          return false;
        }
      }
    }
    return true;
  }

  public static boolean isValid(char[][] board, int row, int col, char c) {
    for (int i = 0; i < 9; i++) {
      if (board[i][col] == c)
        return false;

      if (board[row][i] == c)
        return false;

      if (board[3 * (row / 3) + i / 3][3 * (col / 3) + i % 3] == c)
        return false;
    }
    return true;
  }
}
```
