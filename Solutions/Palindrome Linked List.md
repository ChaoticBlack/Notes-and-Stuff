Given the `head` of a singly linked list, return `true` _if it is a_ _palindrome_ _or_ `false` _otherwise_.

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
    bool isPalindrome(ListNode* head) {
        ListNode* fast=head;
        ListNode* slow=head;
        while(fast && fast->next)
        {
            fast=fast->next->next;
            slow=slow->next;
        }
        //now slow is in the middle, reverse LL from the middle
        ListNode* prev = NULL;
        while(slow)
        {
            ListNode* temp = slow->next;
            slow->next=prev;
            prev=slow;
            slow=temp;
        }
        //after reversing prev will be at the last node, so traverse towards left from there as head traverses to right.
        while(prev)
        {
            if(head->val!=prev->val)
                return false;
            head=head->next;
            prev=prev->next;
        }
        return true;
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
- Can be solved a little easily by storing the LL in an array and checking if array is a palindrome but then space complexity becomes O(n) and not sure if interviewer will like it.
- Points to note in the above solution:
	- When we reverse the LL from the middle, the second half is equal to the first half if LL is palindrome.
	- After reversing the LL, prev will be at the last node hence can be used to traverse from right to left.
- Basic problem, revise well.

### Tags
#easy #LinkedList #TwoPointers 