Given the `root` of a binary tree and an integer `targetSum`, return _the number of paths where the sum of the values along the path equals_ `targetSum`.

The path does not need to start or end at the root or a leaf, but it must go downwards (i.e., traveling only from parent nodes to child nodes).

## Solution
```audio-player
[[Path Sum III.mp3]]
```

## My Code

- ### Faulty Code
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
    int pathSum(TreeNode* root, int targetSum) {
        int res=0;
        dfs(root,0,targetSum,res);
        return(res);
    }
    void dfs(TreeNode* root, int currSum, int targetSum,int& res)
    {
        if(!root)
            return;
        currSum=currSum+root->val;
        if(currSum==targetSum)
            res++;
        dfs(root->left,0,targetSum,res);
        dfs(root->right,0,targetSum,res);
        dfs(root->left,currSum,targetSum,res);
        dfs(root->right,currSum,targetSum,res);
    }
};
```

- ### Correct Code
```cpp
class Solution {
public:
    int pathSum(TreeNode* root, int targetSum) {
        if (!root)
            return 0;
        int res = 0;
        dfs(root, targetSum, 0, res);
        res += pathSum(root->left, targetSum);
        res += pathSum(root->right, targetSum);
        return res;
    }
    void dfs(TreeNode* root, int targetSum, long long currSum, int& res) {
        if (!root)
            return;
        currSum += root->val;
        if (currSum == targetSum)
            res++;
        dfs(root->left, targetSum, currSum, res);
        dfs(root->right, targetSum, currSum, res);
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
- Vey good question, try solving again from scratch while practicing. It has nuances that are better understood if solved.

### Tags
#medium #BinaryTree #DepthFirstSearch 