Merge two sorted arrays without using extra space in C
Here, in this page we will discuss the program to Merge two sorted arrays without using extra space in C . We are given two sorted arrays. We need to merge these two arrays such that the initial numbers (after complete sorting) are in the first array and the remaining numbers are in the second array. Extra space allowed in O(1).

Input: arr1[] = {1, 5, 9, 10, 15, 20};

             arr2[] = {2, 3, 8, 13};

Output: arr1[] = {1, 2, 3, 5, 8, 9}

               arr2[] = {10, 13, 15, 20}

Merge two sorted arrays without using extra space in C
Algorithm :
Take the size of first array from the user and store it in variable say m.
Now, declare an array of size m and take m elements of the array from the user.
Take another variable say n to hold the size of second array and take its value from the user.
Now, declare an array of size n and take n elements from the user.
Now call the function merge that perform the required operations in O(1) space.
Inside merge(),
Iterate through every element of arr2[] starting from last element.

Do following for every element arr2[i]

 Store last element of ar1[i]: last = arr1[i] 

Loop from last element of arr1[] while element arr1[j] is greater than arr2[i]. arr1[j+1] = arr1[j] // Move element one position ahead j–

If any element of arr1[] was moved or (j != m-1) arr1[j+1] = arr2[i]  and  arr2[i] = last

Merging two arra in C
Related Pages
Given an array which consists of only 0, 1 and 2

Find the “Kth” max and min element of an array

Find the Union and Intersection of the two sorted arrays

Find Largest sum contiguous Subarray

Minimize the maximum difference between heights 

Code in C
// C program to merge two sorted
// arrays with O(1) extra space.
#include <stdio.h>


void merge(int arr1[], int arr2[], int m, int n)
{
  // Iterate through all elements
  // of ar2[] starting from the last element
  for (int i = n - 1; i >= 0; i--)
  {
    /* Find the smallest element greater than ar2[i].
    Move all elements one position ahead till the
    smallest greater element is not found */
    int j, last = arr1[m - 1];

    for (j = m - 2; j >= 0 && arr1[j] > arr2[i]; j--)
      arr1[j + 1] = arr1[j];

    // If there was a greater element
    if (j != m - 2 || last > arr2[i])
    {
       arr1[j + 1] = arr2[i];
       arr2[i] = last;
    }
  }
}

// Driver program
int main()
{ 

   int m, n;


scanf("%d", &m);

   int arr1[m];

   for(int i=0; i<m; i++) scanf("%d", &arr1[i]);
   
   scanf("%d", &n);

   int arr2[n];

   for(int i=0; i<n; i++) scanf("%d", &arr2[i]);

   merge(arr1, arr2, m, n);

   printf("After Merging nFirst Array: ");

   for (int i = 0; i < m; i++)
     printf("%d  ", arr1[i] );

   printf( "\nSecond Array: ");

   for (int i = 0; i < n; i++)
   printf("%d  ", arr1[i] );


   return 0;
}
Input :

6
1 5 9 10 15 20 
4
2 3 8 13 

Output :

After Merging 
First Array: 1 2 3 5 8 9 
Second Array: 10 13 15 20 
