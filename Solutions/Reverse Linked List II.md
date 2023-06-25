Given the `head` of a singly linked list and two integers `left` and `right` where `left <= right`, reverse the nodes of the list from position `left` to position `right`, and return _the reversed list_.

## Solution
```audio-player
[[Reverse Linked List II.mp3]]
```

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
    ListNode* reverseBetween(ListNode* head, int left, int right) {
        //phase 1
        ListNode* dummy = new ListNode(0,head);
        ListNode* behindCurr=dummy;
        ListNode* curr=head;
        for(int i=1;i<left;i++)
        {
            behindCurr=curr;
            curr=curr->next;
        }
        //phase 2
        ListNode* prev=NULL;
        for(int i=0;i<right-left+1;i++)
        {
            ListNode* temp = curr->next;
            curr->next=prev;
            prev=curr;
            curr=temp;
        }
        //phase 3
        behindCurr->next->next=curr;
        behindCurr->next=prev;
        return dummy->next;
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
- This and many other LL questions benefit from using a dummy pointer that is to the left of head.
- The advantage is that you don't have to deal with edge cases where head might be NULL or some other node has become the new node.
- No harm in using this technique even when such edge cases don't exist.
- Watch neetcode video if my explanation is not clear, it is a good question, give it importance,

### Tags
#medium #LinkedList 