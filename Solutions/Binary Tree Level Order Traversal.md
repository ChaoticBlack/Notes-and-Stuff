Given the `root` of a binary tree, return _the level order traversal of its nodes' values_. (i.e., from left to right, level by level).

## Solution
Level order traversal is done using the ***Breadth First Search*** Algorithm. For that a queue is used.
- FIrst push the root in the queue. 
- Then while queue is not empty, you pop the first element, add it to current level vector and add its children to the queue.
- To make sure you only tackle one level nodes per iteration of the while loop, at the beginning of the iteration you find the lengh of the queue and just loop through the first `len` elements of the queue, ignoring all the newly added elements .
- Kinda sexy when you think about it.


## My Code

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> result;
        queue<TreeNode*> q;
        q.push(root);
        while(!q.empty())
        {
            vector<int> temp;
            int len = q.size(); // number of nodes at current level
            for(int i=0;i<len;i++)//so that only nodes at current level are considered and not the newer children nodes that will be added
            {
                TreeNode* node=q.front();
                q.pop();
                if(node!=NULL)  //have to check this because we are pushing left and right children without checking if the are null, easier to check in one place than 2 different places
                {
                    temp.push_back(node->val);
                    q.push(node->left); //left before right
                    q.push(node->right);
                }
            }
            if (temp.size()!=0)
            {
                result.push_back(temp);
            }
        }
        return result;
    }
};
```

## Complexity
- Time - O(n)
- Space - O(n)   // because at any time in the queue at most n/2 elements would be present


## Ideal Code
same as above


## My Notes

- adding the children from left to right is important.
- This is a standard question, remember it.


### Tags
#medium #BinaryTree #BreadthFirstSearch