**Simple Search🦌** <br>
simple search is a search algorithm used to look for an element in an array or a list. <br><br>

**Time Complexity** <br>
The time complexity of a simple search is O(n) i.e. Linear time <br> <br>

**Explanation** <br>
In order to look for an x element in the simple search we have to check every element in the list, 
e.g. if there are 10 elements in the list we have to check each element and see if it matches the element which we are looking for. <br>

And in the worst case, that element can be at the end of the list, so for n elements 
(where n is the number of elements in a list), we have to do n operation on a list. So that's what the O(n) stands for. <br><br>

**code**<br>
```
import java.util.Scanner;

public class SimpleSearch {

    public static void main(String[] args) {
        int[] arr = {1,2,3,4,5,6,7,8,9,10};
        int search = takeInputFromUser();
        System.out.print(simpleSearch(search, arr));
    }

    public static boolean simpleSearch(int num, int[] arr) {
        for(int value : arr)
            if(value == num)
                return true;

        return false;
    }

    public static int takeInputFromUser() {
        Scanner scan = new Scanner(System.in);
        return scan.nextInt();
    }
}
```
