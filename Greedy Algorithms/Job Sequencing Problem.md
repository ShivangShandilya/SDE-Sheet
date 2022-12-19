Problem - [Job Sequencing Problem](https://practice.geeksforgeeks.org/problems/job-sequencing-problem-1587115620/1#)

- You are given a set of N jobs where each job comes with a deadline and profit. The profit can only be earned upon completing the job within its deadline. Find the number of jobs done and the maximum profit that can be obtained. Each job takes a single unit of time and only one job can be performed at a time.

- Example 1:

      Input: N = 4, Jobs = {(1,4,20),(2,1,10),(3,1,40),(4,1,30)}

      Output: 2 60

Explanation: The 3rd job with a deadline 1 is performed during the first unit of time .The 1st job is performed during the second unit of time as its deadline is 4.
Profit = 40 + 20 = 60

- Example 2:

      Input: N = 5, Jobs = {(1,2,100),(2,1,19),(3,2,27),(4,1,25),(5,1,15)}

      Output: 2 127

Explanation: The  first and third job both having a deadline 2 give the highest profit. 
Profit = 100 + 27 = 127

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
import java.io.*;
import java.lang.*;
import java.util.*;

class Job {
   int id, profit, deadline;
   Job(int x, int y, int z) {
      this.id = x;
      this.deadline = y;
      this.profit = z;
   }
}

class solve {
   // return an array of size 2 having the 0th element equal to the count
   // and 1st element equal to the maximum profit
   int[] JobScheduling(Job arr[], int n) {
      Arrays.sort(arr, (a, b) -> (b.profit - a.profit));

      int maxi = 0;
      for (int i = 0; i < n; i++) {
         if (arr[i].deadline > maxi) {
            maxi = arr[i].deadline;
         }
      }

      int result[] = new int[maxi + 1];

      for (int i = 1; i <= maxi; i++) {
         result[i] = -1;
      }

      int countJobs = 0, jobProfit = 0;

      for (int i = 0; i < n; i++) {

         for (int j = arr[i].deadline; j > 0; j--) {

            // Free slot found 
            if (result[j] == -1) {
               result[j] = i;
               countJobs++;
               jobProfit += arr[i].profit;
               break;
            }
         }
      }

      int ans[] = new int[2];
      ans[0] = countJobs;
      ans[1] = jobProfit;
      return ans;

   }
}
class Main {
   public static void main(String[] args) throws IOException {

      //size of array
      Job[] arr = new Job[4];
      arr[0] = new Job(1, 4, 20);
      arr[1] = new Job(2, 1, 10);
      arr[2] = new Job(3, 2, 40);
      arr[3] = new Job(4, 2, 30);

      solve ob = new solve();

      //function call
      int[] res = ob.JobScheduling(arr, 4);
      System.out.println(res[0] + " " + res[1]);

   }
}
```
