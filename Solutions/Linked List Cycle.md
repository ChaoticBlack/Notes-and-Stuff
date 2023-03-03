Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that `pos` is not passed as a parameter**.

Return `true` _if there is a cycle in the linked list_. Otherwise, return `false`.

## Solution
```audio-player
[[Linked List Cycle.wav]]
00:00:17 --- Solution
00:00:12 --- Problem Explanation
00:01:18 --- Other related problems 
```

## My Code

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
    
        // if head is NULL then return false;
        if(head == NULL)
            return false;
        
        // making two pointers fast and slow and assignning them to head
        ListNode *fast = head;
        ListNode *slow = head;
        
        // till fast and fast-> next not reaches NULL
        // we will increment fast by 2 step and slow by 1 step
        while(fast != NULL && fast ->next != NULL)
        {
            fast = fast->next->next;
            slow = slow->next;
            
            
            // At the point if fast and slow are at same address
            // this means linked list has a cycle in it.
            if(fast == slow)
                return true;
        }
        
        // if traversal reaches to NULL this means no cycle.
        return false;
    }
};
```

## Complexity
- Time - O(n)
- Space - O(1)


## Ideal Code
similar to above code, just slightly better

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        ListNode* fast= head;
        ListNode* slow=head;
        int flag=0;
        while(fast && fast->next)
        {
            fast=fast->next->next;
            slow=slow->next;
            if(fast==slow)
            {
                flag=1;
                break;
            }
        }
        if(flag) //loop exists
        {
            ListNode* check =head;
            while(fast!=check)
            {
                fast=fast->next;    //slowly iterate fast
                if(fast==slow)
                    check=check->next;
            }
            return check;
        }
        return NULL;
    }
};
```

## Complexity
- Time - O(n)
- Space - O(1)


## My Notes
Fast and Slow Pointer is Key

### Tags
#easy #LinkedList 