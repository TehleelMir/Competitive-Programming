**Longest Palindromic Substring🖌**<br>
Leet code link: https://leetcode.com/problems/longest-palindromic-substring/ <br><br>

Two different solutions with two different time complexities <br><br>

**O(n^3)** <br>
For a string n (where n is the size of string), the below code will generate/check every possible substring and on each of that substrings, it will check if its 
a palindrome which will take O(n/2) Or o(n). So for generating every possible substring simple brute force will take O(n^2) and since on each substring im checking if its 
a palindrome that will take O(n). Combining the both we get O(n^3)
<br><br>
**Code**<br>
```
class Solution {
    public String longestPalindrome(String s) {
        String s2 = "";
        
        for(int i = 0; i < s.length(); i++) {
            String temp = "";
            String temp2 = "";
            for(int j = i; j < s.length(); j++) {
                temp += s.charAt(j);
                if(isPalindrome(temp)) {
                    temp2 = temp;
                }
            }
            if(temp2.length() > s2.length())
                s2 = temp2;
        }
        return s2;
    }
    
    public boolean isPalindrome(String str) {
        for(int i = 0, j = str.length()-1; i < str.length(); i++, j--) 
            if(str.charAt(i) != str.charAt(j))
                return false;
        return true;
    }
}
```
<br><br>

**O(n^2)**<br>
At the top im going through all the elements in a string so O(n) for that. And on each loop im going to go through the whole string again (in the worst case) for that 
another O(n). Combining both we get O(n^2). 
<br><br>
**Code**<br>
```
class Solution {
    int low, max;
    public String longestPalindrome(String s) {
        for(int i=0; i<s.length(); i++) {
            expendFromMiddle(s, i, i);    // for the even case TENET
            expendFromMiddle(s, i, i+1); //  for the odd case TEET
            if(max == s.length()) break;
        }
        return s.substring(low, max+low);
    }
    
    public void expendFromMiddle(String s, int left, int right) {
        while(left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
            left--; 
            right++;
        }
        
        if(max < right-left-1) {
            low = left+1;
            max = right-left-1;
        }
    }
}
```
