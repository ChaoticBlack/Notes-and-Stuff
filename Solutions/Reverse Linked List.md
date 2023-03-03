Given the `head` of a singly linked list, reverse the list, and return _the reversed list_.


## Solution
Just watch neetcode.

## My Code

#### Iterative Approach
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
    ListNode* reverseList(ListNode* head) {
        ListNode* curr = head;
        ListNode* prev = NULL;
        while(curr->next)
        {
            ListNode* temp = curr->next;
            curr->next=prev;
            prev=curr;
            curr=temp;
        }
        return curr;
    }
};

    ListNode* reverseList(ListNode* head) {
        ListNode *nextNode, *prevNode = NULL;
        while (head) {
            nextNode = head->next;
            head->next = prevNode;
            prevNode = head;
            head = nextNode;
        }
        return prevNode;

```


#### Recursive Approach
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
    ListNode* reverseList(ListNode* head) {

        ListNode* prev=NULL;
        reverse(head,prev);
        return prev;
        
        
    }
    void reverse(ListNode* &head,ListNode* &prev )
    {
        if(!head)
            return;
        ListNode* post=head->next;
        head->next=prev;
        prev=head;
        head=post;
        reverse(head,prev);
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
Revise Revise Revise.
Also look up recursion approach when you revise

### Tags
#easy #LinkedList