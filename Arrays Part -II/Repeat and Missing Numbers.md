Problem - [Repeat and Missing Numbers](https://www.interviewbit.com/problems/repeat-and-missing-number-array/)

- You are given a read-only array of N integers with values also in the range [1, N] both inclusive. Each integer appears exactly once except A which appears twice and B which is missing. The task is to find the repeating and missing numbers A and B where A repeats twice and B is missing.

Example 1:

    Input Format:  array[] = {3,1,2,5,3}

    Result: {3,4)

Explanation: A = 3 , B = 4 
Since 3 is appearing twice and 4 is missing

Example 2:

    Input Format: array[] = {3,1,2,5,4,6,7,5}

    Result: {5,8)

Explanation: A = 5 , B = 8 
Since 5 is appearing twice and 8 is missing

- Solution

Disclaimer: Don’t jump directly to the solution, try it out yourself first.

```
static int x, y;
 
    static void getTwoElements(int arr[], int n)
    {
        /* Will hold xor of all elements
       and numbers from 1 to n  */
        int xor1;
 
        /* Will have only single set bit of xor1 */
        int set_bit_no;
 
        int i;
        x = 0;
        y = 0;
 
        xor1 = arr[0];
 
        /* Get the xor of all array elements  */
        for (i = 1; i < n; i++)
            xor1 = xor1 ^ arr[i];
 
        /* XOR the previous result with numbers from
       1 to n*/
        for (i = 1; i <= n; i++)
            xor1 = xor1 ^ i;
 
        /* Get the rightmost set bit in set_bit_no */
        set_bit_no = xor1 & ~(xor1 - 1);
 
        /* Now divide elements into two sets by comparing
    rightmost set bit of xor1 with the bit at the same
    position in each element. Also, get XORs of two
    sets. The two XORs are the output elements. The
    following two for loops serve the purpose */
        for (i = 0; i < n; i++) {
            if ((arr[i] & set_bit_no) != 0)
                /* arr[i] belongs to first set */
                x = x ^ arr[i];
 
            else
                /* arr[i] belongs to second set*/
                y = y ^ arr[i];
        }
        for (i = 1; i <= n; i++) {
            if ((i & set_bit_no) != 0)
                /* i belongs to first set */
                x = x ^ i;
 
            else
                /* i belongs to second set*/
                y = y ^ i;
        }
        
        // at last do a linear check which amont x and y is missing or repeating 
 
        /* *x and *y hold the desired output elements */
    }
```
