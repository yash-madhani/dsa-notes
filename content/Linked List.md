
# MEDIUM PROBLEMS

## Middle of a LinkedList 
https://leetcode.com/problems/middle-of-the-linked-list/description/

Approach: 
1. Calculate length and go to middle.
2. Use slow and fast Algorithm. 
```
class Solution {
    public ListNode middleNode(ListNode head) {

        ListNode slow = head;
        ListNode fast = head;

        while(fast != null && fast.next != null)
        {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
        
    }
}
```

## Reverse a LinkedList 
https://leetcode.com/problems/reverse-linked-list/

Approach: 
1. Use a stack and change the values.
2. Use prev, and next variables to manipulate the links.
```
class Solution {
    public ListNode reverseList(ListNode head) {
        if(head == null || head.next == null) return head;

        ListNode temp = head;
        ListNode prev = null;
        while(temp != null)
        {
            ListNode next = temp.next;
            temp.next = prev;
            prev = temp;
            temp = next;
        }

        head = prev;
        return head;
    }
}
```

## Detect a loop in LL
https://leetcode.com/problems/linked-list-cycle/description/

Approaches: 
1. Use hashmap and traverse, if seen before then return true.
```
public class Solution {
    public boolean hasCycle(ListNode head) {
        if(head == null || head.next == null) return false;

        HashMap<ListNode,Integer> mpp = new HashMap<>();
        ListNode temp = head;

        while(temp != null)
        {
            if(mpp.containsKey(temp))
            {
                return true;
            }
            else
            {
                mpp.put(temp,1);
            }
            temp = temp.next;
        }
        return false;
    }
}
```

2. Use slow-fast algorithm. See the intuition in striver's video
```
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while(fast != null && fast.next != null)
        {
            slow = slow.next;
            fast = fast.next.next;
            if(slow == fast) return true;
        }
        return false;
    }
}
```

## Find the starting point of a loop in LL
https://leetcode.com/problems/linked-list-cycle-ii/description/

Approaches: 
1. Use HashMap. 
2. Use slow-fast Algorithm. Intuition in Striver's Video.
```
public class Solution {
    public ListNode detectCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while(fast != null && fast.next != null)
        {
            slow = slow.next;
            fast = fast.next.next;
            if(slow == fast)
            {
                slow = head;
                while(slow != fast)
                {
                    slow = slow.next;
                    fast = fast.next;
                }
                return slow;
            }
        }
        return null;
    }
}
```

## Check if LL is palindrome or not
https://leetcode.com/problems/palindrome-linked-list/

Approach: Reverse and compare
```
class Solution {
    public ListNode reverseList(ListNode head) {
        if(head == null || head.next == null) return head;
        ListNode temp = head;
        ListNode follow = null;
        while(temp != null)
        {
            ListNode x = temp.next;
            temp.next = follow;
            follow = temp;
            temp = x;
        }
        head = follow;
        return head;
    }

    public boolean isPalindrome(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;

        while(fast.next != null && fast.next.next != null)
        {
            slow = slow.next;
            fast = fast.next.next;
        }
        ListNode newhead = reverseList(slow.next);

        ListNode first = head;
        ListNode second = newhead;

        while(second != null)
        {
            if(first.val != second.val) return false;
            second = second.next;
            first = first.next;
        }
        return true;
    }
}
```
## Segregate odd and even nodes in LL
https://leetcode.com/problems/odd-even-linked-list/

Approach: Make 2 LL, one for odd, other from even, then connect them
```
class Solution {
    public ListNode oddEvenList(ListNode head) {
        if(head == null || head.next == null) return head;

        ListNode odd = head;
        ListNode even = head.next;
        ListNode evenhead = head.next;

        while(even != null && even.next != null)
        {
            odd.next = odd.next.next;
            even.next = even.next.next;

            odd = odd.next;
            even = even.next;
        }
        odd.next = evenhead;
        
        return head;
    }
}
```

## Remove Nth Node From End of List
https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/

Approaches:
1. Count and remove
2. Use 2 pointers - WATCH VIDEO
```
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if(head == null || head.next == null) return null;

        ListNode fast = head;
        ListNode slow = head;

        for(int i=0;i<n;i++) fast = fast.next;

        if(fast == null)
        {
            head = head.next;
            return head;
        }

        while(fast.next != null)
        {
            slow = slow.next;
            fast = fast.next;
        }

        slow.next = slow.next.next;
        return head;
    }
}
```

## Delete the Middle Node of a Linked List
https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/description/

Approaches: 
1. Find middle using slow fast, and go one node before the node to be deleted.
```
class Solution {
    public ListNode deleteMiddle(ListNode head) {
        if(head == null || head.next == null) return null;
        ListNode slow = head;
        ListNode fast = head;
        fast = fast.next.next; // NOTE THIS

        while(fast != null && fast.next != null)
        {
            fast = fast.next.next;
            slow = slow.next;
        }
        System.out.println(slow.val);
        slow.next = slow.next.next;

        return head;
    }
}
```

