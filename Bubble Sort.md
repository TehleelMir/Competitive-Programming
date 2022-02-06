**Bubble Sort🐱‍👤**<br>
Bubble sort is a sorting algorithm used to sort an array/list<br><br>

**Time Complexity**<br>
In the worst case, the time complexity of a bubble sort is O(n²) and in the best case its O(n).<br><br>

**Explanation**<br>
The bubble sort is almost the same as the selection sort, but in the selection sort, the time complexity remains the same in all the cases (best, average, and worst).
While as in bubble sort in the best cases i.e. when the array/list is already sorted time complexity will be O(n) because of the flag which we use in bubble sort. That
flag helps us to check whether the list is already sorted or not. And in the case of selection sort no matter whether the list is sorted or not it will still run the same number
of operations on the list. <br><br>

**Code**
```
import java.util.Arrays;

public class BubbleSort {
    public static void main(String[] args) {
        int[] arr = {3,2,5,9,2,2,9,0};
        bubbleSort(arr);
        System.out.println(Arrays.toString(arr));
    }

    public static void bubbleSort(int[] arr) {
        boolean flag;
        for(int i=0; i<arr.length; i++) {
            flag = false;
            for(int j=1; j<arr.length - i; j++) {
                if(arr[j-1] > arr[j]) {
                    int temp = arr[j-1];
                    arr[j-1] = arr[j];
                    arr[j] = temp;
                    flag = true;
                }
            }
            if(!flag) break;
        }
    }
}
```
