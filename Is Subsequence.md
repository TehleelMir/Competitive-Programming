**Is Subsequence🏍**<br<br>

Leet code link: https://leetcode.com/problems/is-subsequence/ <br><br>

**Time Complexity of below solution**<br>
**O(n)** well we are going through the whole string only once that's why O(n), the below program can be improved to O(n/2) by traversing the string both from front and back. 

<br><br>
**Code**<br>
```
class Solution {
    public boolean isSubsequence(String s, String t) {
        if(s.isEmpty()) return true;
        
        for(int i=0, j=0; i<t.length() && j<s.length(); i++) 
            if(t.charAt(i) == s.charAt(j)) 
                if(++j == s.length()) return true;
        
        return false;   
    }
}
```
