## Solution
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }
        
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode pre = dummy;
        
        while (pre.next != null && pre.next.next != null) {
            if (pre.next.val == pre.next.next.val) {
                int sameName = pre.next.val;
                while (pre.next != null && pre.next.val == sameName) {
                    ListNode delNode = pre.next;
                    pre.next = delNode.next;
                    delNode.next = null;
                }
            } else {
                pre = pre.next;
            }          
        }
        return dummy.next;
    }
}
```