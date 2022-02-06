**Quick Sort📜**<br>
Not so quick actually, but yeah this algorithm is used to sort an array/list.<br><br>

**Time Complexity**<br>
- Average case O(n Log n)
- Worst case O(n²).
<br><br>

**Explanation**<br>
At the top two main operations are happing in the quick sort, one is the partition which places an element to its fixed position, and that operation takes 
O(n). 
And second is the actual divide and conquer which in the best/average case will divide the list into two parts, and perform the same operation on either side of the partition.<br>
So, considering the above lines in the mind, in the best/average case quicksort will take O(n * n/2), where first n is from the first operation and n/2 from the divide and conquer
which we can also write as O(n log n). <br><br>
And in the worst case, which is when the array/list is already sorted and we are using 0 or n-1 index of the list as a pivot (where n is the size of the list),
in that case, the time complexity will be O(n²),
because again two operations will be happing the first will remain the same but the divide and conquer one won't be happing because the list is already sorted and at each level, we
are just creating only one side of the partition, and it will happen for all the elements, so the second operation will also take O(n). Combining both the operation we get O(n²).
<br>
<br>
There are two recommendations to avoid the worst case. <br>
- Always use the middle index as the pivot
- Choose the pivot Randomly.
<br><br>

**Code**<br>
```
import java.util.Arrays;

public class QuickSort {
    public static void main(String[] args) {
        int[] arr = {3,5,9,99,0,1,5,2};
        quickSort(arr, 0, arr.length-1);
        System.out.print(Arrays.toString(arr));
    }

    public static void quickSort(int[] arr, int low, int high) {
        if(low > high) return;
        int pivot = partition(arr, low, high);
        quickSort(arr, low, pivot-1);
        quickSort(arr, pivot+1, high);
    }

    public static int partition(int[] arr, int low, int high) {
        //low will be our pivot
        int nextPivot = low+1;
        for(int i=nextPivot; i<=high; i++)
            if(arr[i] < arr[low])
                swap(arr, i, nextPivot++);
        swap(arr, low, nextPivot-1);
        return nextPivot-1;
    }

    public static void swap(int[] arr, int _this, int _withThis) {
        int temp = arr[_this];
        arr[_this] = arr[_withThis];
        arr[_withThis] = temp;
    }
}
```
