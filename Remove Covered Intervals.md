**Remove Covered Intervals🚲**<br><br>

Leet code link: https://leetcode.com/problems/remove-covered-intervals/ <br><br>

Two different solutions with two different time complexities, but the second solution will have two different versions both using the same algorithm but the one is using the sort function provided by the language and the other one is using merge sort which is written in the code.  <br> <br>

**O(n^2)**<br>
In the below code, I'm checking every pair in an array using brute force, so O(n^2) for that. 
<br><br>
**Code**<br>
```
class Solution {
    public int removeCoveredIntervals(int[][] intervals) {
        int size = intervals.length;
        
        for(int i=0; i<intervals.length; i++) {
            int[] arr = intervals[i];
            int one = arr[0];
            int two = arr[1];
            
            for(int j=0; j<intervals.length; j++) {
                if(i == j) continue;
                int[] brr = intervals[j];
                int oneb = brr[0];
                int twob = brr[1];
                
                if(oneb <= one && twob >= two) {
                    size--;
                    break;
                }
            }
        }
        return size;
    }
}
```
<br><br>
**O(sort)**<br>
In the below coding snippets im sorting an array by the first value in ascending order if the values are equal, then im sorting them using the right values by descending order, and depending upon the sort complexities same time complexity will be applied for the whole algorithm as well, yes there is a loop also which goes through the whole array at the end, but as per the Big O rule "Drop non-dominate terms" and since sorting will obviously take more then O(n) that's why im ignoring that second loop. <br>
<br>
In the first version i have used Java's inner sorting function, which i don't know which sorting technique it is using, but its faster then the merge sort i have written in the second example. 
<br><br>
**Code**<br><br>
**Version 1**<br>
```
class Solution {
    public int removeCoveredIntervals(int[][] i) {
        Arrays.sort(i, new customComparator());
        int result = 0, right = 0;
        for(int[] x : i)
            if(x[1] > right) {
                result++;
                right = x[1];
            }
        return result;
    }
}

class customComparator implements Comparator<int[]> {
    @Override
    public int compare(int[] val1, int[] val2) {
        if(val1[0] > val2[0]) return 1; 
        if(val1[0] < val2[1]) return -1;
        
        if(val1[1] < val2[1]) return 1;
        if(val1[1] > val2[1]) return -1;
        
        return 0;
    }
}
```
<br><br>
**Version 2**<br>
```
class Solution {
    public int removeCoveredIntervals(int[][] i)  {
        mergeSort(i, 0, i.length-1);
        int result = 0, right = 0;
        for(int[] x : i)
            if(x[1] > right) {
                result++;
                right = x[1];
            }
        return result;
    }

    void mergeSort(int[][] i, int left, int right) {
        if(left < right) {
            int mid = (left + right) / 2;
            mergeSort(i, left, mid);
            mergeSort(i, mid+1, right);
            merge(i, left, mid, right);
        }
    }

    void merge(int[][] brr, int left, int mid, int right) {
        int[][] arr = new int[brr.length+1][2]; 
        int i = left, j = mid+1, k = 0; 
        
        while(i <= mid && j <= right) {
            int one = brr[i][0];
            int two = brr[i][1];
            int oneB = brr[j][0];
            int twoB = brr[j][1];
            
            if(one < oneB) {
                arr[k++] = brr[i++];
            }
            else if(oneB < one) {
                arr[k++] = brr[j++];
            }
            else if(two > twoB) {
                arr[k++] = brr[i++];
            } 
            else if(twoB > two) {
                arr[k++] = brr[j++];
            }
        }
        
        while(i <= mid)
            arr[k++] = brr[i++];
        while(j <= right)
            arr[k++] = brr[j++];
        
        k=0;
        while(left <= right)
            brr[left++] = arr[k++];
    }
}
```
