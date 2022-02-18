**Longest Substring Without Repeating Characters📸**<br><br>

Leet code link: https://leetcode.com/problems/longest-substring-without-repeating-characters/ <br> <br>

I have written 3 different solution for the same problem, with 3 different time complexities. <br> <br>

**O(n^2)**<br>
In the below code im traversing through all the characters in a string, and it is just a basic operation it will take O(n) time (where n is the size of string). 
But on each loop im changing the loop value if a certain condition comes true, at the end i will still go through all the characters of a string but may not only once. In the worst-case i have to traverse n-1 characters for a single character which will again take O(n) time, and since this operation will be applied to each character
individually, it will take O(n) * O(n) time or O(n^2).
<br>
**Code**<br>
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashMap<Character, Integer> map = new HashMap<>();
        int top = 0, x = 0;
        
        for(int i=0; i<s.length(); i++) {
            Character temp = s.charAt(i);
            if(map.containsKey(temp)) {
                top = Math.max(top, x);
                i = map.get(temp);
                map.clear();
                x = 0;
                continue;
            }
            map.put(temp, i);
            x++;
        }
        return Math.max(top, x);
    }
}
```
<br><br>
**O(2n)**<br>
The below code is using a sliding window algorithm/technique. Again Outer loop will go through all the characters in a string, so O(n) is the time for that. And the inner 
loop in the worst case it has to touch every character in a string. Now it may seem that this algorithm also takes O(n) * O(n) or o(n^2) time but it isn't.
In the above coding solution we were modifying the value of the outer loop so in the worst case it has to go through n-1 characters for a single character, but here both the outer
and the inner loop has to travel n times through the whole string in the worst case i.e. O(n) + O(n) or (O 2n). 
Again in the worst case, both inner and outer loops will have to go through 
all the characters of a string its, not like that inner loop will have to go through all the elements in a string for a single character. No that's not the case here. 
<br>
**Code**<br>
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashSet<Character> set = new HashSet();
        int max = 0;
        
        for(int i=0, j=0; i<s.length(); i++) {
            char c = s.charAt(i);
            if(set.contains(c)) {
                while(set.contains(c))
                    set.remove(s.charAt(j++));
            }
            set.add(c);
            max = Math.max( max , (i-j)+1 );
        }
        
        return max;
    }
}
```
<br><br>
**O(n)**<br>
Well here there is only one loop that goes through the whole string only once, so O(n) or linear time.
<br>
**Code**<br>
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashMap<Character, Integer> map = new HashMap<>();
        int max = 0;
        
        for(int i=0, j=0; i<s.length(); i++) {
            char c = s.charAt(i);
            
            if(map.containsKey(c)) 
                j = Math.max( j , map.get(c)+1 );    
                
            map.put(c, i);
            max = Math.max( max , (i-j)+1 );
        }
        
        return max;
    }
}
```
