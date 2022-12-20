Problem - [Find minimum number of coins](https://www.geeksforgeeks.org/find-minimum-number-of-coins-that-make-a-change/)

- Given a value V, if we want to make a change for V Rs, and we have an infinite supply of each of the denominations in Indian currency, i.e., we have an infinite supply of { 1, 2, 5, 10, 20, 50, 100, 500, 1000} valued coins/notes, what is the minimum number of coins and/or notes needed to make the change.

- Example 1:

      Input: V = 70

      Output: 2

Explaination: We need a 50 Rs note and a 20 Rs note.

- Example 2:

      Input: V = 121

      Output: 3

Explaination: We need a 100 Rs note, a 20 Rs note and a 1 Rs coin.


- Solution:

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
import java.util.*;
public class Main {
  public static void main(String[] args) {

    int V = 49;
    ArrayList < Integer > ans = new ArrayList < > ();
    int coins[] = {1, 2, 5, 10, 20, 50, 100, 500, 1000};
    int n = coins.length;
    for (int i = n - 1; i >= 0; i--) {
      while (V >= coins[i]) {
        V -= coins[i];
        ans.add(coins[i]);
      }
    }
    System.out.println("The minimum number of coins is "+ans.size());
    System.out.println("The coins are ");
    for (int i = 0; i < ans.size(); i++) {
      System.out.print(" " + ans.get(i));
    }

  }
}
```
