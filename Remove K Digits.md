**Remove K Digits💼**<br>
Leet code link: https://leetcode.com/problems/remove-k-digits/ <br><br>

I have written two solutions for the same problem with two different time complexities <br><br>

**O(kn)**<br>
Where k is the number of elements that can be removed from a string, and n is the size of that string<br>
For each k'th position im going through n elements each time, so K * N <br>

**Code**<br>
```
class Solution {
    public String removeKdigits(String num, int k) {
        StringBuilder result = new StringBuilder(num);
        
        for(int j = 0; j < k; j++) {
            int i = 0;
            while(i < result.length()-1 && result.charAt(i) <= result.charAt(i+1)) 
                i++;
            result.deleteCharAt(i);
        }
        
        while(result.length() > 0 && result.charAt(0) == '0')
            result.deleteCharAt(0);
        
        if(result.length() == 0) 
            return "0";
        
        return result.toString();
        
    }
}
```
<br><br>
**O(n)**<br>
In the below code it may not seem that the time complexity of the below code can't be N because of that nested loop, well the outer loop is going to go through all the 
elements so O(n) for that, and the inner loop in the worst case will go through all the elements in a string but only once, so combining the two we get 
O(2n), dropping the constant value we have O(n). <br><br> 
You may think there are other loops as well in the code, for that you need to remember following 4 rules of Big :O <br>
- If you have two different steps in your algorithm, you should add up those steps
- Drop the constants (in most cases they do matter)
- Different inputs, different variables (like k and n in the above code)
- Drop non-dominate terms


**Code** <br>
```
class Solution {
    public String removeKdigits(String num, int k) {
        Stack<Character> stack = new Stack<Character>();
        
        for(int i = 0; i < num.length(); i++) {
            char c = num.charAt(i);
            
            while(!stack.empty() && k > 0 && stack.peek() > c) {
                stack.pop();
                k--;
            }
            
            if(!stack.empty() || c != '0') 
                stack.push(c);
        }
        
        while(!stack.empty() && k-- > 0)
            stack.pop();
        
        if(stack.empty()) 
            return "0";
        
        StringBuilder str = new StringBuilder("");
        for(char temp : stack) 
            str.append(temp);
        
        return str.toString();
    }
}
```
