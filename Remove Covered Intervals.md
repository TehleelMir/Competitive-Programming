**Remove Covered Intervals🚲**<br><br>

Leet code link: https://leetcode.com/problems/remove-covered-intervals/ <br><br>

Two different solution with two different time complexities, but the second solution will have two different version both using the same algorithm but the one is using 
library sort provided by the language and the other one is using merge sort which is writtern in the code.  <br> <br>

**O(n^2)**<br>
In the below code, im checking every pair in an array using the brute fource, so O(n^2) for that. 
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
            if(one == -1 && two == -1) continue;
            
            for(int j=0; j<intervals.length; j++) {
                if(i == j) continue;
                int[] brr = intervals[j];
                int oneb = brr[0];
                int twob = brr[1];
                
                if(oneb <= one && twob >= two) {
                    size--;
                    intervals[i][0] = -1;
                    intervals[i][1] = -1;
                    break;
                }
            }
        }
        return size;
    }
}

O(n^2) for above code.




```
