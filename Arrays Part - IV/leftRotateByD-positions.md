## Left rotate an array by D places
**Problem Statement**: Given an array of N integers and an integer D, left rotate the array by D place.
<br>

- Example 1:
```
Input: N = 7, array[] = {1,2,3,4,5,6,7} , d = 3
Output: 4 5 6 7 1 2 3
Explanation: The array is rotated to the left by 3 positions.
```

- Example 2:
```
Input: N = 6, array[] = {3,7,8,9,10,11} , d = 2 
Output: 8 9 10 11 3 7
Explanation: The array is rotated to the left by 2 positions.
```

#### Approach: `Brute Force`

<img src="https://github.com/Sohoxic/SDE-Sheet/blob/main/Arrays%20Part%20-%20IV/assets/images/BruteForce.png">

```
import java.util.*;

public class Main {

    public static void leftRotateArrayByOne(int arr[], int n, int d) {
        if(n == 0) return;
        int d_new = d % n;
        int[] new_arr = new int[d_new];
        if(n > 1 && d < n) {
            for(int j = 0; j < d_new; j++) {
                new_arr[j] = arr[j];
                System.out.print(new_arr[j] + " ");
            }
            System.out.println();
            
            for(int i = 0; i < n - d; i++) {
                arr[i] = arr[i + d];
            }
            int i = 0;
            for(int j = n - d; j < n; j++) {
                arr[j] = new_arr[i];
                i++;
            }
        }
        for(int i = 0; i < n; i++) {
            System.out.print(arr[i] + " ");
        }
    }

    public static void main(String[] args) {
        int n = 5;
        int d = 3;
        int[] arr = {1, 2, 3, 4, 5};
        leftRotateArrayByOne(arr, n, d);
    }
}


```

#### Approach: `Optimal Approach`

<img src="https://github.com/Sohoxic/SDE-Sheet/blob/main/Arrays%20Part%20-%20IV/assets/images/OptimalApproach.png">

```

import java.util.*;

public class Main {

    public static void reverse(int arr[], int start, int end) {
        while(start <= end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            end--;
            start++;
        }
    }

    public static void leftRotate(int arr[], int n, int d) {
        if(n == 0) return;
        d = d % n;
        reverse(arr, 0, d - 1);
        reverse(arr, d, n - 1);
        reverse(arr, 0, n - 1);
    }

    public static void main(String[] args) {
        int n = 7;
        int[] arr = {1, 2, 3, 4, 5, 6, 7};
        int d = 3;

        System.out.println("Before rotation:");
        for(int i = 0; i < n; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();

        leftRotate(arr, n, d);

        System.out.println("After rotation:");
        for(int i = 0; i < n; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();
    }
}
```

