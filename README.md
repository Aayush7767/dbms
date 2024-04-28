Selection Sort
#include <stdio.h>
void selectionSort(int arr[], int size);
void swap(int *a, int *b);
/*Selection sort function*/
void selectionSort(int arr[], int size)
{
int i, j;
for (i = 0; i < size; i++)
{
for (j = i; j < size; j++)
{
if (arr[i] > arr[j])
swap(&arr[i], &arr[j]);
}
}
}
/*Function to swap two variables*/
void swap(int *a, int *b)
{
int temp;
temp = *a;
*a = *b;
*b = temp;
}
/*Main Function*/
int main()
{
int array[10], i, size;
printf("How many numbers you want to sort: ");
scanf("%d", &size);
printf("\nEnter %d numbers:\t", size);
printf("\n");
for (i = 0; i < size; i++)
scanf("%d", &array[i]);
selectionSort(array, size);
printf("\nSorted array is: ");
for (i = 0; i < size; i++)
printf(" %d ", array[i]);
return 0;
}


Insertion Sort.
#include <stdio.h>
int main(void)
{
int n, i, j, temp;
int arr[64];
printf("\nEnter number of elements:");
scanf("%d", &n);
printf("\nEnter %d integers:\t\n", n);
for (i = 0; i < n; i++)
{
scanf("%d", &arr[i]);
}
for (i = 1; i < n; i++)
{
j = i;
while (j > 0 && arr[j - 1] > arr[j])
{
temp = arr[j];
arr[j] = arr[j - 1];
arr[j - 1] = temp;
j--;
}
}
printf("\nSorted array is:");
for (i = 0; i < n; i++)
{
printf(" %d ", arr[i]);
}
return 0;
}


Merge Sort
#include <stdio.h>
#include <stdlib.h>
// merge function
void Merge(int arr[], int left, int mid, int right)
{
int i, j, k;
int size1 = mid - left + 1;
int size2 = right - mid;
// created temporary array
int Left[size1], Right[size2];
// copying the data from arr to temporary array
for (i = 0; i < size1; i++)
Left[i] = arr[left + i];
for (j = 0; j < size2; j++)
Right[j] = arr[mid + 1 + j];
// merging of the array
i = 0; // intital index of first subarray
j = 0; // inital index of second subarray
k = left; // initial index of parent array
while (i < size1 && j < size2)
{
if (Left[i] <= Right[j])
{
arr[k] = Left[i];
i++;
}
else
{
arr[k] = Right[j];
j++;
}
k++;
}
// copying the elements from Left[], if any
while (i < size1)
{
arr[k] = Left[i];
i++;
k++;
}
// copying the elements from Right[], if any
while (j < size2)
{
arr[k] = Right[j];
j++;
k++;
}
}
// merge sort function
void Merge_Sort(int arr[], int left, int right)
{
if (left < right)
{
int mid = left + (right - left) / 2;
// recursive calling of merge_sort
Merge_Sort(arr, left, mid);
Merge_Sort(arr, mid + 1, right);
Merge(arr, left, mid, right);
}
}
// driver code
int main()
{
int size;
printf("\nEnter the size: ");
scanf("%d", &size);
int arr[size];
printf("\nEnter the elements of array:\t\n ");
for (int i = 0; i < size; i++)
{
scanf("%d", &arr[i]);
}
Merge_Sort(arr, 0, size - 1);
printf("\nThe sorted array is: ");
for (int i = 0; i < size; i++)
{
printf(" %d ", arr[i]);
}
printf("\n");
return 0;
}



Quick Sort
#include <stdio.h>
#include <stdlib.h>
int quickSort(int *arr, int low, int high)
{
int i = low, j = high;
int pivot = arr[(low + high) / 2];
while (i <= j)
{
while (arr[i] < pivot)
i++;
while (arr[j] > pivot)
j--;
if (i <= j)
{
int temp = arr[i];
arr[i] = arr[j];
arr[j] = temp;
i++;
j--;
}
}
if (low < j)
quickSort(arr, low, j);
if (i < high)
quickSort(arr, i, high);
return 0;
}
int main(void)
{
puts("Enter the number of elements in the array: ");
int n;
scanf("%d", &n);
int arr[n];
puts("Enter the elements of the array: ");
for (int i = 0; i < n; i++)
{
printf("arr[%d]: ", i);
scanf("%d", &arr[i]);
}
int low = 0;
int high = n - 1;
int pivot = arr[high];
int k = low - 1;
for (int j = low; j < high; j++)
{
if (arr[j] <= pivot)
{
k++;
int temp = arr[k];
arr[k] = arr[j];
arr[j] = temp;
}
}
int temp = arr[k + 1];
arr[k + 1] = arr[high];
arr[high] = temp;
int pi = k + 1;
quickSort(arr, low, pi - 1);
quickSort(arr, pi + 1, high);
puts("The sorted array is: ");
for (int i = 0; i < n; i++)
{
printf("%d ", arr[i]);
}
return 0;
}



Max Min
#include<stdio.h>
int max, min;
int a[100];
void maxmin(int i, int j)
{
    int max1, min1, mid;
    if(i==j)
    {
        max = min = a[i];
    }
    else
    {
        if(i == j-1)
        {
            if(a[i] < a[j])
            {
                max = a[j];
                min = a[i];
            }
            else
            {
                max = a[i];
                min = a[j];
            }
        }
        else
        {
            mid = (i+j)/2;
            maxmin(i, mid);
            max1 = max; 
            min1 = min;
            maxmin(mid+1, j);
            if(max < max1)
                max = max1;
            if(min > min1)
                min = min1;
        }
    }
}
int main ()
{
    int i, num;
    printf ("\nEnter the total number of numbers : ");
    scanf ("%d", &num);
    printf ("Enter the numbers : \n");
    for (i = 1; i <= num; i++)
        scanf ("%d", &a[i]);

    max = a[1];
    min = a[1];
    maxmin(1, num);
    printf ("Minimum element in the array : %d\n", min);
    printf ("Maximum element in the array : %d\n", max);
    return 0;
}



Fractional Knapsack
#include <stdio.h>
void main()
{
int capacity, no_items, cur_weight, item;
int used[10];
float total_profit;
int i;
int weight[10];
int value[10];
printf("\nEnter the capacity of knapsack:");
scanf("%d", &capacity);
printf("\nEnter the number of items:");
scanf(" %d", &no_items);
printf("\nEnter the weight and value respectively of %d item:\n",
no_items);
for (i = 0; i < no_items; i++)
{
printf("Weight[%d]:\t", i);
scanf("%d", &weight[i]);
printf("Value(Rs.)[%d]:\t", i);
scanf("%d", &value[i]);
}
for (i = 0; i < no_items; ++i)
used[i] = 0;
cur_weight = capacity;
while (cur_weight > 0)
{
item = -1;
for (i = 0; i < no_items; ++i)
if ((used[i] == 0) &&
((item == -1) || ((float)value[i] / weight[i] >
(float)value[item] / weight[item])))
item = i;
used[item] = 1;
cur_weight -= weight[item];
total_profit += value[item];
if (cur_weight >= 0)
printf("Added object %d (%d Rs., %dKg) completely in the
bag. Space left: %d.\n", item + 1, value[item], weight[item],
cur_weight);
else
{
int item_percent = (int)((1 + (float)cur_weight /
weight[item]) * 100);
printf("Added %d%% (%d Rs., %dKg) of object %d in the
bag.\n", item_percent, value[item], weight[item], item + 1);
total_profit -= value[item];
total_profit += (1 + (float)cur_weight / weight[item]) *
value[item];
}
}
printf("Filled the bag with objects worth %.2f Rs.\n",
total_profit);
}


 Floyd Warshall Algorithm 
#include <stdio.h>
#include <stdlib.h>
void floydWarshall(int **graph, int n)
{
int i, j, k;
for (k = 0; k < n; k++)
{
for (i = 0; i < n; i++)
{
for (j = 0; j < n; j++)
{
if (graph[i][j] > graph[i][k] + graph[k][j])
graph[i][j] = graph[i][k] + graph[k][j];
}
}
}
}
int main(void)
{
int n, i, j;
printf("Enter the number of vertices: ");
scanf("%d", &n);
int **graph = (int **)malloc((long unsigned) n * sizeof(int *));
for (i = 0; i < n; i++)
{
graph[i] = (int *)malloc((long unsigned) n * sizeof(int));
}
for (i = 0; i < n; i++)
{
for (j = 0; j < n; j++)
{
if (i == j)
graph[i][j] = 0;
else
graph[i][j] = 100;
}
}
printf("Enter the edges: \n");
for (i = 0; i < n; i++)
{
for (j = 0; j < n; j++)
{
printf("[%d][%d]: ", i, j);
scanf("%d", &graph[i][j]);
}
}
printf("The original graph is:\n");
for (i = 0; i < n; i++)
{
for (j = 0; j < n; j++)
{
printf("%d ", graph[i][j]);
}
printf("\n");
}
floydWarshall(graph, n);
printf("The shortest path matrix is:\n");
for (i = 0; i < n; i++)
{
for (j = 0; j < n; j++)
{
printf("%d ", graph[i][j]);
}
printf("\n");
}
return 0;
}


LCS
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
// Function to find the longest common subsequence
void lcs(const char *str1, const char *str2, int len1, int len2)
{
int lcsTable[len1 + 1][len2 + 1]; // LCS table for dynamic
programming
int i, j;
// Initialize the table with 0s
for (i = 0; i <= len1; i++)
{
for (j = 0; j <= len2; j++)
{
if (i == 0 || j == 0)
{
lcsTable[i][j] = 0;
}
}
}
// Fill the LCS table
for (i = 1; i <= len1; i++)
{
for (j = 1; j <= len2; j++)
{
if (str1[i - 1] == str2[j - 1])
{
lcsTable[i][j] = lcsTable[i - 1][j - 1] + 1; // Extend
the common subsequence
}
else
{
lcsTable[i][j] = (lcsTable[i - 1][j] > lcsTable[i][j -
1]) ? lcsTable[i - 1][j] : lcsTable[i][j - 1]; // Choose the maximum
}
}
}
// Find the LCS by backtracking
int index = lcsTable[len1][len2]; // Length of LCS
char lcsStr[index + 1]; // Array to store the LCS
lcsStr[index] = '\0'; // Null-terminate the string
i = len1;
j = len2;
while (i > 0 && j > 0)
{
if (str1[i - 1] == str2[j - 1])
{
lcsStr[--index] = str1[i - 1]; // Include the matching
character
i--;
j--;
}
else if (lcsTable[i - 1][j] > lcsTable[i][j - 1])
{
i--; // Move upwards in the table
}
else
{
j--; // Move leftwards in the table
}
}
printf("The Longest Common Subsequence is: %s\n", lcsStr);
}
int main()
{
char str1[100], str2[100]; // Buffers to store the input strings
printf("Enter the first sequence: ");
fgets(str1, sizeof(str1), stdin); // Read the first sequence
str1[strcspn(str1, "\n")] = '\0'; // Remove newline character
printf("Enter the second sequence: ");
fgets(str2, sizeof(str2), stdin); // Read the second sequence
str2[strcspn(str2, "\n")] = '\0'; // Remove newline character
int len1 = strlen(str1);
int len2 = strlen(str2);
lcs(str1, str2, len1, len2); // Find the LCS of the two sequences
return 0;
}
