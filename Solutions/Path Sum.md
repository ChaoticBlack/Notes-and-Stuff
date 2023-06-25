Given the `root` of a binary tree and an integer `targetSum`, return `true` if the tree has a **root-to-leaf** path such that adding up all the values along the path equals `targetSum`.

A **leaf** is a node with no children.

## Solution
```audio-player
[[Path Sum.mp3]]
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
    bool hasPathSum(TreeNode* root, int targetSum) {
        if(!root)
            return false;
        return(dfs(root,0,targetSum));
    }
    bool dfs(TreeNode* root, int currSum, int targetSum)
    {
        if(!root)
            return false;

		currSum=currSum+root->val;
        if(!root->left && !root->right)  //current node is leaf node
        {
            if(currSum==targetSum)
                return true;
            return false;
        }
        return(dfs(root->left,currSum,targetSum) || dfs(root->right,currSum,targetSum));
    }
};
```

## Complexity
- Time - O(n)
- Space - O(1)


## Ideal Code
similar to above code

## Complexity
- Time - O(n)
- Space - O(1)


## My Notes
- DFS can take things from leaf to root or from root to leaf. Both directions are useful depending on the problem.
- In this problem we take sum from root to leaf.

### Tags
#easy #BinaryTree #DepthFirstSearch 