## Solution1
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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode pre = dummy;
        ListNode cur = dummy.next;
        int len = 0;
        while (cur != null) {
            cur = cur.next;
            len++;
        }
        cur = dummy.next;
        for (int i = 0; i < len - n; i++) {
            cur = cur.next;
            pre = pre.next;
        }
        pre.next = cur.next;
        cur.next = null;
        return dummy.next;
    }
}
```
## Solution2: follow up : one pass
tricky
使用快慢指针来置换位置

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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if (head == null) return head;
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode cur = dummy.next;
        ListNode fast = dummy;
        ListNode slow = dummy;
        for (int i = 0; i <= n; i++) {
            fast = fast.next;
        }
        while (fast != null) {
            slow = slow.next;
            fast = fast.next;
        }
        ListNode del = slow.next;
        slow.next = del.next;
        del.next = null;
        return dummy.next;
    }
}
```