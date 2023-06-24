
You are given a **perfect binary tree** where all leaves are on the same level, and every parent has two children. The binary tree has the following definition:

```cpp
struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
```
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to `NULL`.

Initially, all next pointers are set to `NULL`.
## Solution
```audio-player
[[Populating Next Right Pointers in Each Node.mp3]]
```

## My Code

```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* left;
    Node* right;
    Node* next;

    Node() : val(0), left(NULL), right(NULL), next(NULL) {}

    Node(int _val) : val(_val), left(NULL), right(NULL), next(NULL) {}

    Node(int _val, Node* _left, Node* _right, Node* _next)
        : val(_val), left(_left), right(_right), next(_next) {}
};
*/

class Solution {
public:
    Node* connect(Node* root) {
        if(!root)
            return root;
        queue<Node*> q;
        q.push(root);
        while(q.size()!=0)
        {
            int len = q.size();
            for(int i=0;i<len;i++)
            {
                Node* curr = q.front();
                q.pop();
                if(curr)
                {
                    if(i!=len-1) //means the current element is not the last element of current level
                        curr->next=q.front();
                    else
                        curr->next=NULL;
                    q.push(curr->left);
                    q.push(curr->right);
                }
            }
        }
        return root;
    }
};
```

## Complexity
- Time - O(n)
- Space - O(n)


## Ideal Code
went over my head, watch neetcode if you want.
## Complexity
- Time - O(n)
- Space - O(1)


## My Notes
- Level order traversal.

### Tags
#medium #BinaryTree #BreadthFirstSearch 