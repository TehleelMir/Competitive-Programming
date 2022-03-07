**Merge Two Sorted Lists🚚**<br><br>

Leet code link: https://leetcode.com/problems/merge-two-sorted-lists/ <br><br>

Two different solutions with the same time complexity, the first solution is using the iteration method and the second one is using the recursive method. <br><br>

Time Complexity<br><br>
**O(m+n)**, where m is the size of the first list and n is the size of the second. In the first solution, we are looping through all the elements in both lists, and in the 
second solution, we are using recursion to move between all the items in both lists.<br><br>


**Solution 1**<br>
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
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode head = new ListNode();
        ListNode temp = head;
        
        while(list1 != null && list2 != null) {
            if(list1.val < list2.val) {
                temp.next = list1;
                list1 = list1.next;
            }
            else {
                temp.next = list2;
                list2 = list2.next;
            }
            temp = temp.next;
        }
       
        if(list1 != null)
            temp.next = list1;
        else if(list2 != null)
            temp.next = list2;
        
        return head.next;
    }
}
```
<br><br>

**Solution 2**<br>
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
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if(l1 == null) return l2;
        if(l2 == null) return l1;
        
        if(l1.val < l2.val) {
            l1.next = mergeTwoLists(l1.next, l2);
            return l1;
        }
        else {
            l2.next = mergeTwoLists(l1, l2.next);
            return l2;
        }
    }
}
```

