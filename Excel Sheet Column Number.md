**Excel Sheet Column Number🏍**<br><br>
Leet Code Link: https://leetcode.com/problems/excel-sheet-column-number/ <br> <br>

**Time Complexity for the below solution is O(n), looping through the whole string only once**<br><br>

**Code**<br>
```
class Solution {
    public int titleToNumber(String c) {
        //ZB => (Z*26)+B
        if(c.length() < 2) return (c.charAt(0) - 65) + 1;
        int x = (c.charAt(0) - 65) + 1;
        
        for(int i=0; i<c.length()-1; i++) 
            x = (x * 26) + (c.charAt(i+1) - 65) + 1;
        
        return x;
    }
}
```
