**Merge Sort🎂**<br>
Merge sort is a sorting algorithm used to sort an array/list.<br><br>

**Time Complexity**<br>
The time complexity of the merge case is O(n log n) in all the cases.<br><br>

**Explanation**<br>
In merge sorted we use the divide and conquer method to divide the whole list into sub-partitions until each partition only contains one element,
so that takes O(log n) time. Second, on each level of the Recursion tree, we perform the merge operation that goes through the n elements in the list 
and sorted them, so that takes O(n). So combining both operations we get O(n log n).<br><br>

Ps: The below code has a time complexity of O(n² log n) and not (n log n), because on each level of Recursion I'm 
also creating a new array first then adding the elements in it in the sorted order. And then again copying back those elements in the original array
in the same order, so what I'm saying is I'm going through each element in the array two time and not just once, which of course can be improved. <br><br>


**Code**<br>
```
import java.util.Arrays;

public class MergeSort {
    public static void main(String[] args) {
        int[] arr = {4,22,-1,93,1,98,233,-235,0,0};
        mergeSort(arr, 0, arr.length-1);
        System.out.print(Arrays.toString(arr));
    }

    public static void mergeSort(int[] arr, int low, int high) {
        if(low < high) {
            int mid = (low + high) / 2;
            mergeSort(arr, low, mid);
            mergeSort(arr, mid + 1, high);
            merge(arr, low, mid, high);
        }
    }

    public static void merge(int[] arr, int low, int mid, int high) {
        int[] brr = new int[(high - low) + 1];
        int i = low, j = mid+1, k = 0;

        while(i <= mid && j <= high)
            if(arr[i] < arr[j])     brr[k++] = arr[i++];
            else                    brr[k++] = arr[j++];

        while(i <= mid)
            brr[k++] = arr[i++];
        while(j <= high)
            brr[k++] = arr[j++];

        k=0;
        while(low <= high)
            arr[low++] = brr[k++];

    }
}
```
