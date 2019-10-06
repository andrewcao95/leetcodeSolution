## Solution
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null) {
            return null;
        }
        ListNode a = headA;
        ListNode b = headB;
        int lenA = getLength(headA);
        int lenB = getLength(headB);
        
        if (lenA > lenB) {
            while (lenA != lenB) {
                a = a.next;
                lenA--;
            }
        } else if (lenB > lenA) {
            while (lenA != lenB) {
                b = b.next;
                lenB--;
            }
        }
        while (a != b) {
            a = a.next;
            b = b.next;
        }
        return a;
    }
    
    public int getLength(ListNode head) {
        ListNode cur = head;
        int len = 0;
        while (cur != null) {
            len++;
            cur = cur.next;
        }
        return len;
    }
}
```