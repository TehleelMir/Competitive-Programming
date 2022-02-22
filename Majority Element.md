**Majority Element🏎**<br><br>

Leet Code Link: https://leetcode.com/problems/majority-element/
<br><br>

Four different solutions with 4 different time/space complexities <br><br>

**O(n^2)**<br>
For each element going through the whole array, so O(n^2)
<br>
<br>
**Code**<br>
```
class Solution {
    public int majorityElement(int[] nums) {
        int m = nums.length / 2;
        
        for(int i=0; i<nums.length; i++) {
            int x = nums[i];
            int count = 0;
            for(int j=0; j<nums.length; j++) {
                if(x == nums[j]) {
                    count++;
                }
            }
            if(count > m) return x;
        }
        
        return 0;
    }
}
```
<br><br>
**O(n)**<br>
Going throught the whole array only once, so O(n)
<br>
<br>
**Code**<br>
```
class Solution {
    public int majorityElement(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();
        
        for(int i=0; i<nums.length; i++)
            if(map.containsKey(nums[i])) { 
                map.replace(nums[i], map.get(nums[i])+1);
                if(map.get(nums[i]) > nums.length/2)
                    return nums[i];
            } else
                map.put(nums[i], 1);
        
        return nums[0];
    }
}
```
<br><br>
**O(n log n)**<br>
Sorting takes O(n log n) time to sort the list, so O(n log n)
<br>
<br>
**Code**<br>
```
class Solution {
    public int majorityElement(int[] nums) {
        Arrays.sort(nums);
        return nums[nums.length/2];
    }
}
```
<br><br>

**O(n) && O(1) for space complexity**<br>
Going through the array only once, and maintaining the space constant by not using any extra array or hashmap with the help of Boyer-Moore Voting Algorithm ( yeah i also can't pronounce
it)
<br><br>
**Code**<br>
```
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0;
        int result = 0;
        
        for(int x : nums) {
            if(count == 0) result = x;
            count += (x == result)? 1 : -1;
        }
        
        return result;
    }
}
```
