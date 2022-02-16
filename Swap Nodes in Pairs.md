**Swap Nodes in Pairs💰**<br>

Leet code link: https://leetcode.com/problems/swap-nodes-in-pairs/ <br><br>

*Time complexity*<br>
**O(n/2)**<br>
For example, if I have a list that has 7 nodes in it, then it will have 3 pairs and one extra node in total, and the loop will run only 3 times, so O(n/2) <br>
I know we usually ignore constants in Big O, but sometimes they do matter. If I have a list of 1 million nodes as input for this question, the below code will  
loop through half-million times only, so writing it as O(n) would be correct, that's what I think.<br><br>

**Code**<br>
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
    public ListNode swapPairs(ListNode head) {
        if(head == null || head.next == null) return head;
        
        ListNode secondNode = head.next;
        ListNode temp = head;
        
        while(temp != null && temp.next != null) {
            ListNode a = temp;
            ListNode b = temp.next;
            ListNode x1 = a;
            ListNode x2 = b.next;
            
            a = b;
            b = x1;
            a.next = b;
            
            if(x2 == null)
                b.next = x2;
            else if(x2.next != null)
                b.next = x2.next;
            else
                b.next = x2;
            
            temp = x2;
            
        }
        return secondNode;
    }
}
```
