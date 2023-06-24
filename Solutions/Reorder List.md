You are given the head of a singly linked-list. The list can be represented as:

L0 → L1 → … → Ln - 1 → Ln

_Reorder the list to be on the following form:_

L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …

You may not modify the values in the list's nodes. Only nodes themselves may be changed.

## Solution

## My Code

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    void reorderList(ListNode* head) {
        if(!head || !head->next)
            return;
        ListNode* fast = head;
        ListNode* slow = head->next;
        ListNode* behind = NULL;
        //find the element just before middle(behind pointer)
        while(fast && fast->next)
        {
            behind=slow;
            fast=fast->next->next;
            slow=slow->next;
        }
        //now behind is at the middle of the list, reverse the LL from middle
        ListNode* prev = NULL;
        while(behind)
        {
            ListNode* temp = behind->next;
            behind->next=prev;
            prev=behind;
            behind=temp;
        }
        // traverse both halfs of LL together and connect one node after other
        ListNode* l1 = head;
        ListNode* l2 = prev;
        while(l2->next)
        {
            ListNode* temp2 = l2->next;
            ListNode* temp1 = l1->next;
            l1->next=l2;
            l2->next=temp1;
            l2=temp2;
            l1=temp1;
        }
    }
};
```

## Complexity
- Time - O(n)
- Space - O(1)


## Ideal Code
same as above
## Complexity
- Time - O(n)
- Space - O(1)

## My Notes
- Find the element just one element behind the middle and from that point reverse the LL.
- Now we basically have two LL, we have to connect the elements alternatingly to get our answer.
- The base condition is important or else you get runtime error if LL only has 1 node.
- To approach such problems, use pen and paper, see how things work and step by step write the code. Most LL problems are some sort of combination of basic LL problems just slightly twisted, so keep basics clear.
- Watch neetcode if solution not clear.

### Tags
#medium #LinkedList #TwoPointers 