Problem - [Merge K Sorted Arrays](https://www.codingninjas.com/codestudio/problems/merge-k-sorted-arrays_975379?leftPanelTab=2)

- You have been given 'K' different arrays/lists, which are sorted individually ( in ascending order ). You need to merge all the given arrays/list such that the output array/list should be sorted in ascending order.

- Sample Input 1:

      1
      2
      3 
      3 5 9 
      4 
      1 2 3 8   

- Sample Output 1:

      1 2 3 3 5 8 9 

Explanation Of Sample Input 1:

After merging the two given arrays/lists [3, 5, 9] and [ 1, 2, 3, 8], the output sorted array will be [1, 2, 3, 3, 5, 8, 9].

- Sample Input 2:

      1
      4
      3
      1 5 9
      2
      45 90
      5
      2 6 78 100 234
      1
      0

- Sample Output 2:

      0 1 2 5 6 9 45 78 90 100 234

Explanation Of Sample Input 2 :

After merging the given arrays/lists [1, 5, 9], [45, 90], [2, 6, 78, 100, 234] and [0], the output sorted array will be [0, 1, 2, 5, 6, 9, 45, 78, 90, 100, 234].

- Solution

```
/*
    Time Complexity: O((N * K) * log(K)) 
    Space Complexity: O(N * K)
    
    Where N is the total number of elements in all the arrays, and K is the number of arrays.
*/

// import java.util.*;

import java.util.HashSet;
import java.util.ArrayList;
import java.util.Comparator;
import java.util.Collections;
import java.util.PriorityQueue;


class Pair 
{
    public int first, second, third;

    Pair(int first, int second, int third) 
    {
        this.first = first;
        this.second = second;
        this.third = third;
    }
}


// Implements Comparator interface for min-heap.
class PqComparator implements Comparator<Pair> 
{
    public int compare(Pair pair1, Pair pair2) 
    {
        if (pair1.first < pair2.first) 
        {
            return -1;
        }
        if (pair1.first == pair2.first) 
        {
            return 0;
        }
        return 1;
    }
}

public class Solution 
{

    public static ArrayList<Integer> mergeKSortedArrays(ArrayList<ArrayList<Integer>> kArrays, int k) 
    {
        ArrayList<Integer> result = new ArrayList<Integer>();

        // Create a min heap to store atmost k heap nodes at a time.
        PriorityQueue<Pair> minHeap = new PriorityQueue < Pair>(new PqComparator());

        for (int i = 0; i < kArrays.size(); i++) 
        {
            minHeap.add(new Pair( kArrays.get(i).get(0), i, 0 ));
        }


        while (minHeap.isEmpty() == false) 
        {

            // Remove the minimum element from the heap.
            Pair curr = minHeap.remove();

            // i is the array number and j is the index of the removed element in the ith array.
            int i = curr.second;
            int j = curr.third;

            // Add the removed element to the output array.
            result.add(curr.first);

            // If the next element of the extracted element exists, add it to the heap.
            if (j + 1 < kArrays.get(i).size()) 
            {
                minHeap.add(new Pair( kArrays.get(i).get(j + 1),  i, j + 1 ));
            }
        }

        // Return the output array.
        return result;
    }
}
```
