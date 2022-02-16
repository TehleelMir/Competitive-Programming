**Two Sum🎏**<br>

Leet code link: https://leetcode.com/problems/two-sum/ <br>

I have written 3 solutions for the same problem with three different time complexities. <br> <br>  

**O(n^2) or Quadratic time**<br>
This is a simple solution that uses the Brute Force method to check every possible pair in an array to find the target solution.<br>
The outer loop compares each element to the rest of the n-1 elements, for each element in the array thus time complexity is O(n^2). 
<br><br>
**Code**<br>
```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for(int i=0; i<nums.length; i++) 
            for(int j=i+1; j<nums.length; j++)
                if(nums[i]+nums[j] == target)
                    return new int[] {i, j}; 
        
        return new int[0];
} 
```
<br><br>

**O(n * n/2)**<br>
The below code also uses the brute force method, but the inner loop runs only half the size of the array instead of going through the whole array each time. <br>
Thus the time complexity of the outer loop is O(n) because it goes through the whole array, and the time complexity of the inner loop is O(n/2), combining the both we get 
O(n * n/2) as the time complexity for the below code. <br><br>

**Code**<br>
```
 public int[] twoSum(int[] nums, int target) {
        for(int i=0; i<nums.length; i++)
            for(int k=i+1, j=nums.length-1 ; k<=j ; k++, j--) {
                if(nums[i]+nums[k] == target) return new int[]{i,k};
                if(nums[i]+nums[j] == target) return new int[]{i,j};
            }
        return new int[0];
    }
```

<br><br>
**O(n) or linear time**<br>
The time complexity of below code is O(n), it goes through the whole array only once, this was possible because of the constant time complexity of hashmap
for getting an item out of it.
<br><br>

**Code**<br>
```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for(int i=0; i<nums.length; i++) {
            Integer requiredNumber = target - nums[i];
            if(map.containsKey(requiredNumber)) {
                int indexOfThatNumber = map.get(requiredNumber);
                return new int[]{i, indexOfThatNumber};
            }
            map.put(nums[i], i);
        }   
        return new int[0];
    }
} 
```




























