# Palindrome Linked List
## https://leetcode.com/problems/palindrome-linked-list

Given a singly linked list, determine if it is a palindrome.

Example 1:

Input: 1->2
Output: false

Example 2:

Input: 1->2->2->1
Output: true

**Follow up: Could you do it in O(n) time and O(1) space?**

# Implementation :
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
    public boolean isPalindrome(ListNode head) {
        if(head == null || head.next == null)
            return true;
        
        ListNode p1 = clone(head);
        ListNode p2 = reverse(head);
        while(p1 != null) {
            if(p1.val != p2.val)
                return false;
            p1 = p1.next;
            p2 = p2.next;
        }
        return true;
    }
    
    private ListNode clone(ListNode head) {
        ListNode cloneHead = null;
        ListNode prev = null;
        ListNode current = head;
        while(current != null) {
            ListNode listnode = new ListNode(current.val);
            if(cloneHead == null) {
                cloneHead = listnode;
            }
            if(prev != null) {
                prev.next = listnode;
            }
            prev = listnode;
            current = current.next;
        }
        return cloneHead;
    }
    
    private ListNode reverse(ListNode head) {
        ListNode current = head;
        ListNode prev = null;
        while(current != null) {
            ListNode tmp = current.next;
            current.next = prev;
            prev = current;
            current = tmp;
        }
        return prev;
    }
}
```
