**Add Two Number 📯** <br>
Leet code link: https://leetcode.com/problems/add-two-numbers/ <br><br>

*Time Complexity*<br>
**O(l) or Linear time** (where l is the size of the list that has more nodes in it) <br><br>

**Explanation**<br>
There is only one loop in the code that runs l times, and l is the size of the list which has more nodes in it, e.g. list1 has size 2 and list2 has size 9, the loop
will run 9 times. <br><br>

**Code**
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode head = null, tail = null, temp;
        int carry = 0, n1, n2, sum;
        
        while(l1 != null || l2 != null) {
            if(l1 != null) {
                n1 = l1.val;
                l1 = l1.next;
            } else 
                n1 = 0;
            
            if(l2 != null) {
                n2 = l2.val;
                l2 = l2.next;
            } else
                n2 = 0;
            
            sum = n1 + n2 + carry;
            carry = sum/10;
            
            if(head == null) {
                temp = new ListNode(sum % 10);
                head = tail = temp;
            } else {
                temp = new ListNode(sum % 10);
                tail.next = temp;
                tail = temp;
            }
        }
        
        if(carry > 0) tail.next = new ListNode(carry);
        return head;
    }
}
```
