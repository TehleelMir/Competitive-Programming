**Selection Sort🛫**<br>
selection sort is a sorting algorithm that is used to sort an array/list. <br><br>

**Time Complexity**<br>
The time complexity of the selection sort is O(n²). i.e. Quadratic time.<br><br>

**Explanation**<br>
In Selection sort, we do the following operations:<br>
- First pick an element from a list <br>
- Second we compare that element with the other remaining elements in this list. <br>
- Repeat step first until the list is empty.<br>

So, we have to perform step first for every element in the list, and the time complexity for that is O(n)<br>
And then we have to compare that element with the other remaining elements in the list, and the time complexity for that is O(n - z), 
where z is the number of elements we have already checked, but since we ignore constans in Big O notation, so instead of writing
O(n  - z) we will just write it as O(n)<br>

So we have O(n * n) time complexity for the whole algorithm, which we can also write as O(n²).<br><br>

**Code**<br>
```
import java.util.Arrays;

public class SelectionSort {
    public static void main(String[] args) {
        int[] arr = {5,3,6,8,6,3,35,99,0};
        selectionSort(arr);
        System.out.println(Arrays.toString(arr));
    }

    public static void selectionSort(int[] arr) {
        for(int i=0; i<arr.length-1; i++) {
            int smallIndex = i;
            for(int j=i+1; j<arr.length; j++)
                if(arr[j] < arr[smallIndex])
                    smallIndex = j;

            if(smallIndex != i) {
                int temp = arr[smallIndex];
                arr[smallIndex] = arr[i];
                arr[i] = temp;
            }
        }
    }
 }
```
