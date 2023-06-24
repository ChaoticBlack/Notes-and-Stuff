Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

**Note:** A leaf is a node with no children.

## Solution
```audio-player
[[Minimum Depth of Binary Tree.mp3]]
```

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
    int minDepth(TreeNode* root) {
        if(!root)
            return 0;
        int ans = rec(root);
        return ans;
    }
    int rec(TreeNode* root)
    {
        //base condition
        if(!root->left && !root->right)
            return 1;
        int l=1000000;
        int r=1000000;
        if(root->left)
            l= rec(root->left);
        if(root->right)
            r= rec(root->right);
        return(1+min(l,r));
    }
};
```

## Complexity
- Time - O(n)
- Space - O(n)


## Ideal Code
same as above
## Complexity
- Time - O(n)
- Space - O(n)


## My Notes
- Think before you implement.

### Tags
#easy #BinaryTree #DepthFirstSearch #BreadthFirstSearch 