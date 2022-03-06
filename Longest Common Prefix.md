**Longest Common Prefix🦼**<br><br>

Leet code link: https://leetcode.com/problems/longest-common-prefix/ <br><br>

Two different solution with two different time complexity. <br><br>

**O(n+s)** <br>
where n is the number of items in an array and s is the sum of all the characters given in each item of the array. <br><br>
**Code**<br>
```
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if(strs.length < 1) return "";
        
        String p = strs[0];
        for(int i=1; i<strs.length; i++) 
            p = check(strs[i], p);

        return p;
    }
    
    String check(String s, String p) {
        String temp = "";
        
        for(int i=0, j=0; i<s.length() && j<p.length(); i++, j++) {
            if(s.charAt(i) != p.charAt(j)) break;
            temp += p.charAt(j)+"";
        }
        
        return temp;
    }
}
```
<br><br>

**O(n*m)**<br>
The time complexity is O(n*m) where n is the length of the array and m is the length of the longest string.<br><br>
**Code**<br>
```
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if(strs.length == 0) return "";
        String p = strs[0];
        
        for(int i=1; i<strs.length; i++) 
            while(strs[i].indexOf(p) != 0)
                p = p.substring(0, p.length()-1);
        
        return p;
    }
}
```
