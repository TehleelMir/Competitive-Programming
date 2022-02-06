**Binary Search🌿**<br>
Binary search is a search algorithm used to look for an element in a sorted array/list. <br><br>

**Time Complexity**<br>
The time complexity of a binary search is O(Log n) i.e. Log time or Logarithmic time. In computer science, an empty Log without any base value assigned to it is always equal
to the Log of base 2. <br><br>

**Explanation**<br>
Let's start with a simple search, in simple search we look every element in a list one after another to look for the element which we are looking for, and in the
worst case that element can be at the end of the list, so the time complexity in simple search is Linear time O(n). And in the binary search, we also try to do the same 
thing i.e. searching for a particular element but without checking every element in the list. Instead, we use something known as the divide and conquer rule.<br>
On each step/operation we element half of the list, simply because they don't have the element which we are looking for. <br>
Example:<br>
we have an array that contains **[10]** elements, and on each step, we are eliminating the half array so <br>
on step 1, we eliminated half the array now the array size is **[5]** <br>
on step 2, we did the same thing again, now the array size is **[2]** <br>
on step 3, we apply the same thing again, and now the array size is **[1]** <br><br>

So, for the array size of 10, we just have to perform 3 operations to confirm does the array contains the element which we are looking for or not. 
And that's what the Log n does. Log 10 = 3 apx. 

**code**
```
import java.util.Scanner;

public class BinarySearch {
    public static void main(String[] args) {
        int[] arr = {1,2,3,4,5,6,7,8,9,10};
        int search = takeUsersInput();
        System.out.println(binarySearch(search, arr));
    }

    public static int takeUsersInput() {
        Scanner scan = new Scanner(System.in);
        return scan.nextInt();
    }

    public static boolean binarySearch(int num, int[] arr) {
        int low = 0, high = arr.length-1;
        while(low <= high) {
            int mid = (low+high) / 2;

            if(num == arr[mid])
                return true;
            if(num < arr[mid])   high = mid-1;
            else                 low  = mid+1;
        }
        return false;
    }
}
```
