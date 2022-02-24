**Median of Two Sorted Arrays🚚**<br><br>

Leet code link: https://leetcode.com/problems/median-of-two-sorted-arrays/ <br><br>

Two different solutions with two different time complexities 
<br><br>

**O(n+n2)** where n is the size of array1 and n2 size of array2 <br>
In the worst case, the below code will go through all the elements in both the arrays separately so O(n + n2). 
<br><br>
**Code**<br>
```
class Solution {
    public double findMedianSortedArrays(int[] o, int[] o2) {
        int[] arr = new int[o.length + o2.length];
        int size = arr.length;
        
        int i = 0, j = 0, k = 0;
        while(i < o.length && j < o2.length)
            if(o[i] < o2[j]) arr[k++] = o[i++];
            else             arr[k++] = o2[j++];
        
        while(i < o.length)  arr[k++] = o[i++];
        while(j < o2.length) arr[k++] = o2[j++];
        
        if(size % 2 != 0) return arr[(size / 2)];
        return (arr[(size / 2)-1] + arr[(size / 2)]) / (double)2;
    }
}
```
<br><br>
**O(log min(n,n2))** <br>
If array1 have the less numbers of elements, so the below code will apply binary search method on that array, so O(log x) where x is the size of the array which have less
number of elements. 
<br><br>
**Code**<br>
```
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        if(nums2.length < nums1.length) return findMedianSortedArrays(nums2, nums1);
        int n1 = nums1.length;
        int n2 = nums2.length;
        int low = 0, high = n1;
        
        while(low <= high) {
            int cut1 = (low+high) / 2;
            int cut2 = (n1+n2+1) / 2 - cut1;
            
            int l1 = cut1 == 0 ? Integer.MIN_VALUE : nums1[cut1-1];
            int l2 = cut2 == 0 ? Integer.MIN_VALUE : nums2[cut2-1];
            
            int r1 = cut1 == n1 ? Integer.MAX_VALUE : nums1[cut1];
            int r2 = cut2 == n2 ? Integer.MAX_VALUE : nums2[cut2];
            
            if(l1 <= r2 && l2 <= r1) 
                if((n1 + n2) % 2 == 0)  return (Math.max(l1,l2) + Math.min(r1, r2)) / 2.0;
                else                    return Math.max(l1,l2);
            
            else if(l1 > r2)
                high = cut1 - 1;
            
            else 
                low = cut1 + 1;
        }
        
        return 0.0;
    }
}
```
