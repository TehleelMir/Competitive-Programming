**Valid Parentheses🚕**<br><br>

Leet code link: https://leetcode.com/problems/valid-parentheses/ <br><br>

**Time Complexity**<br>
**O(n)** we are going through the whole string only once, and the insertion and deletion in a stack are constant time. <br><br>

**Code**<br>
```
class Solution {
    public boolean isValid(String s) {
        LinkedList<Character> stack = new LinkedList<>();
        for(int i=0; i<s.length(); i++) {
            char temp = s.charAt(i);
            if(stack.isEmpty()) {
                stack.add(temp);
                continue;
            }
            if(arePair(temp, stack.getLast())) stack.removeLast();
            else stack.add(temp);
        }
        return stack.isEmpty();
    }
    
    boolean arePair(char x, char y) {
        if      (x == ')')   return (y == '(');
        else if (x == ']')   return (y == '[');
        else if (x == '}')   return (y == '{');
        return false;
    }
}
```
