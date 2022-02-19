**Palindrome Number🎙**<br>

Three different solution with three different time complexities <br><br>

**O(n)**<br>
Where n is the number of digits. The reversing of a string will take n steps.

**Code**<br>
```
class Solution {
    public boolean isPalindrome(int x) {
        return (new StringBuilder(x+"")).reverse().toString().equals(x+"");
    }
}
```
<br><br>

**O(n/2)**<br>
Where n is the number of digits.
<br>
**Code**<br>
```
class Solution {
    public boolean isPalindrome(int x) {
        String str = x+"";
        for(int i = 0, j = str.length()-1; i < str.length(); i++, j--) {
            if(str.charAt(i) != str.charAt(j)) 
                return false;
        }
        return true;
    }
}
```
<br><br>

**O(Log base 10 (n))**<br>
Where n is the number itself, in the below program we are trying to get the half number of the actual number, and on each loop, we are dividing out input by 10. 
In other words how many times do we have to divide n by 10 in order to get its half number
<br>
**Code**<br>
```
class Solution {
    public boolean isPalindrome(int x) {
        if(x < 0 || (x % 10 == 0 && x != 0)) return false; 
        
        int halfNumber = 0;
        while(halfNumber < x) {
            halfNumber = (halfNumber * 10) + x%10;
            x /= 10;
        }
        
        return (halfNumber == x || x == halfNumber/10);
    }
}
```

