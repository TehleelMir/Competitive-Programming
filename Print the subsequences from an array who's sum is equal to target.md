Print only those subsequences from an array whos sum is equal to 2 <br><br>

```
import java.util.LinkedList;

public class MyClass {
    public static void main(String args[]) {
      LinkedList<Integer> list = new LinkedList<Integer>();    
      int[] arr = new int[]{1,2,1};
      print(0, arr, 0, list);
    }
    
    static void print(int index, int[] arr, int sum, LinkedList<Integer> list) {
        if(index >= arr.length) {
            if(sum == 2) {
                System.out.println(list.toString());
            }
            return;
        }
        list.add(arr[index]);
        sum += arr[index];
        print(index+1, arr, sum, list);
        sum -= arr[index];
        list.removeLast();
        print(index+1, arr, sum, list);
    }
    
}

```
<br><br>

Print only 1 subsequence from an array whos sum is equal to 2<br><br>
```
import java.util.LinkedList;

public class MyClass {
    public static void main(String args[]) {
      LinkedList<Integer> list = new LinkedList<Integer>();    
      int[] arr = new int[]{1,2,1};
      print(0, arr, 0, list);
    }
    
    static boolean print(int index, int[] arr, int sum, LinkedList<Integer> list) {
        if(index >= arr.length) {
            if(sum == 2) {
                System.out.println(list.toString());
                return true;
            }
            return false;
        }
        list.add(arr[index]);
        sum += arr[index];
        
        if ( print(index+1, arr, sum, list) ) return true;;
        
        sum -= arr[index];
        list.removeLast();
        
        if ( print(index+1, arr, sum, list) ) return true; 
        
        return false;
    }
    
}
```
