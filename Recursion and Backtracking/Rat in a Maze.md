Problem - [Rat in a Maze](https://practice.geeksforgeeks.org/problems/rat-in-a-maze-problem/1)

- Consider a rat placed at (0, 0) in a square matrix of order N * N. It has to reach the destination at (N – 1, N – 1). Find all possible paths that the rat can take to reach from source to destination. The directions in which the rat can move are ‘U'(up), ‘D'(down), ‘L’ (left), ‘R’ (right). Value 0 at a cell in the matrix represents that it is blocked and the rat cannot move to it while value 1 at a cell in the matrix represents that rat can travel through it.

Note: In a path, no cell can be visited more than one time.

Print the answer in lexicographical(sorted) order

Examples:

- Example 1:

      Input:
      N = 4
      m[][] = {{1, 0, 0, 0},
              {1, 1, 0, 1}, 
              {1, 1, 0, 0},
              {0, 1, 1, 1}}

      Output: DDRDRR DRDDRR

Explanation:

<img src = "https://user-images.githubusercontent.com/101946115/209067263-737eb117-5886-45c0-affd-036b7117a599.png" height = 300 width = 300 />

The rat can reach the destination at (3, 3) from (0, 0) by two paths - DRDDRR and DDRDRR, when printed in sorted order we get DDRDRR DRDDRR.

- Example 2:

      Input: N = 2
      m[][] = {{1, 0},
               {1, 0}}

      Output:
      No path exists and the destination cell is blocked.

-Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
import java.util.*;

// m is the given matrix and n is the order of matrix
class Solution {
  private static void solve(int i, int j, int a[][], int n, ArrayList < String > ans, String move,
    int vis[][], int di[], int dj[]) {
    if (i == n - 1 && j == n - 1) {
      ans.add(move);
      return;
    }
    String dir = "DLRU";
    for (int ind = 0; ind < 4; ind++) {
      int nexti = i + di[ind];
      int nextj = j + dj[ind];
      if (nexti >= 0 && nextj >= 0 && nexti < n && nextj < n &&
        vis[nexti][nextj] == 0 && a[nexti][nextj] == 1) {

        vis[i][j] = 1;
        solve(nexti, nextj, a, n, ans, move + dir.charAt(ind), vis, di, dj);
        vis[i][j] = 0;

      }
    }
  }
  public static ArrayList < String > findPath(int[][] m, int n) {
    int vis[][] = new int[n][n];
    for (int i = 0; i < n; i++) {
      for (int j = 0; j < n; j++) {
        vis[i][j] = 0;
      }
    }
    int di[] = {
      +1,
      0,
      0,
      -1
    };
    int dj[] = {
      0,
      -1,
      1,
      0
    };
    ArrayList < String > ans = new ArrayList < > ();
    if (m[0][0] == 1) solve(0, 0, m, n, ans, "", vis, di, dj);
    return ans;
  }
}
class TUF {
  public static void main(String[] args) {

    int n = 4;
    int[][] a = {{1,0,0,0},{1,1,0,1},{1,1,0,0},{0,1,1,1}};

    Solution obj = new Solution();
    ArrayList < String > res = obj.findPath(a, n);
    if (res.size() > 0) {
      for (int i = 0; i < res.size(); i++)
        System.out.print(res.get(i) + " ");
      System.out.println();
    } else {
      System.out.println(-1);
    }
  }
}
```
