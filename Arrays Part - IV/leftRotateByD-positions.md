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
#include<bits/stdc++.h>
using namespace std;

void leftRotateArrayByOne(int arr[], int n, int d){
    if(n==0) return;    
    int d_new = d%n;
    // cout<<d<<endl;
    int new_arr[d_new];
    if(n>1 && d<n){
        for(int j=0;j<d_new;j++){
            new_arr[j] = arr[j];
            cout<<new_arr[j]<<" ";
        }
        cout<<endl;
        
        for(int i=0; i<n-d; i++){
            arr[i] = arr[i+d];
        }

        int i=0;

        for(int j=n-d;j<n;j++){
            arr[j] = new_arr[i];
            i++;
        }
    }

    for(int i=0; i<n;i++){
        cout<<arr[i];
    }
}

int main() {
  int n=5;
  int d=3;
  int arr[]= {1,2,3,4,5};
  leftRotateArrayByOne(arr, n, d);
}

```

#### Approach: `Optimal Approach`

<img src="https://github.com/Sohoxic/SDE-Sheet/blob/main/Arrays%20Part%20-%20IV/assets/images/OptimalApproach.png">

```

#include<bits/stdc++.h>
using namespace std;

void reverse(int arr[], int start, int end){
    while(start<=end){
        // cout<<"before reverse"<<arr[start]<<" "<<arr[end]<<endl;
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        // cout<<arr[start]<<" "<<arr[end]<<endl;
        end--;
        start++;
    }
    // cout<<endl;
}

void leftRotate(int arr[], int n, int d){
    if(n==0) return;
    d = d%n;

    reverse(arr, 0, d-1);

    reverse(arr, d, n-1);

    // cout<<"final reverse";
    reverse(arr, 0, n-1);
}

int main()
{
    int n = 7;
    int arr[] = {1, 2, 3, 4, 5, 6, 7};
    int d = 3;

    cout << "Before rotation:" << endl;
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;

    leftRotate(arr, n, d);
    cout << "After rotation:" << endl;
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
    return 0;
}

