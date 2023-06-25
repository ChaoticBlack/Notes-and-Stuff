Given the `head` of a linked list, reverse the nodes of the list `k` at a time, and return _the modified list_.

`k` is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of `k` then left-out nodes, in the end, should remain as it is.

You may not alter the values in the list's nodes, only nodes themselves may be changed.

## Solution
solve reverse LL 2 and then try this question, its pretty straight forward.

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
    ListNode* reverseKGroup(ListNode* head, int k) {
        ListNode* dummy = new ListNode(0,head);
        ListNode* behindCurr = dummy;
        ListNode* curr=head;
        ListNode* lookAhead = head;
        ListNode* prev=NULL;
        while(1)
        {
            int i=0;
            int numNodes=0;
            while(i<k && lookAhead)
            {
                lookAhead=lookAhead->next;
                numNodes++;
                i++;
            }
            cout<<numNodes<<endl;
            if(numNodes==k)
            {
                reverseSection(curr,prev,k);
                behindCurr->next->next=curr;
                behindCurr->next=prev;
                while(behindCurr->next!=curr)
                    behindCurr=behindCurr->next;
            }
            else
                return dummy->next;
        }
    }
    void reverseSection(ListNode*&  curr,ListNode*& prev, int k)
    {
        
        int i=0;
        while(i<k && curr)
        {
            
            ListNode* temp = curr->next;
            curr->next=prev;
            prev=curr;
            curr=temp;
            i++;
        }
    }
};
```

## Complexity
- Time - O(n)
- Space - O(1)


## Ideal Code

## Complexity
- Time - O(n)
- Space - O(1)


## My Notes


### Tags
#hard #LinkedList 