**Longest Substring Without Repeating Characters📸**<br><br>

Leet code link: https://leetcode.com/problems/longest-substring-without-repeating-characters/ <br> <br>

I have written 3 different solution for the same question, with 3 different time complexities. <br> <br>

**O(n^2)**<br>
stuff.....
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
stuff..
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
stuff...
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
