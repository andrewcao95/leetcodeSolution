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
import java.util.ArrayList;
import java.util.Arrays;

public class Solution {
    public ListNode plusOne(ListNode head) {
        ListNode newHead = reverse(head);
        ListNode cur = newHead;
        int add = 1;
        while (cur != null) {
            int sum = cur.val + add;
            add = sum / 10;
            cur.val = sum % 10;
            cur = cur.next;
        }
        newHead = reverse(newHead);
        if (add != 0) {
            ListNode node = new ListNode(add);
            node.next = newHead;
            newHead = node;
        }
        return newHead;
    }

    public ListNode reverse(ListNode head) {
        ListNode pre = null;
        ListNode cur = head;
        while (cur != null) {
            ListNode temp = cur.next;
            cur.next = pre;
            pre = cur;
            cur = temp;
        }
        return pre;
    }
}
```