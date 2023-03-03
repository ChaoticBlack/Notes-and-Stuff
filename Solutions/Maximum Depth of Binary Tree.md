Given the `root` of a binary tree, return _its maximum depth_.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

## Solution
### Approach 1:
The simplest approach is **recursive DFS**. 
- Figure out the base condition and build on it.
- if there are 0 nodes in binary tree then max len is 0. This is the base condition.
- Recursive equation willl be something like
- `len = 1+max(rec(node->right),rec(node->left)) 

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
    int maxDepth(TreeNode* root) {
        int ans = rec(root);
        return ans;
    }
    int rec(TreeNode* node)
    {
        if(node==NULL)//base case
        {
            return 0;
        }
        return(1+max(rec(node->right),rec(node->left)));
    }
};
```

## Complexity
- Time - O(n)
- Space - O(1)

### Approach 2:
Level order Traversal or BFS
- Basically we are counting the number of levels.

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
    int maxDepth(TreeNode* root) {
        queue<TreeNode*> q;
        q.push(root);
        int count=0;
        while(q.size()!=0)
        {
            int len=q.size();
            for(int i=0;i<len;i++)
            {
                TreeNode* node = q.front();
                q.pop();
                if (node!=NULL)
                {
                    q.push(node->left); 
                    q.push(node->right);
                }
            }
            count++;
        } 
        return count-1;
    }
};
```




## My Notes
Approach 1 is better but approach 2 is more intuitive.