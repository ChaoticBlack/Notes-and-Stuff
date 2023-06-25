Given the `root` of a binary tree and an integer `targetSum`, return _all **root-to-leaf** paths where the sum of the node values in the path equals_ `targetSum`_. Each path should be returned as a list of the node **values**, not node references_.

A **root-to-leaf** path is a path starting from the root and ending at any leaf node. A **leaf** is a node with no children.

## Solution
```audio-player
[[Path Sum II.mp3]]
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
    vector<vector<int>> pathSum(TreeNode* root, int targetSum) {
        vector<vector<int>> res;
        vector<int> path;
        bool temp = dfs(root,0,targetSum,res,path);
        return(res);
    }

    bool dfs(TreeNode* root, int currSum, int targetSum,vector<vector<int>>& res,vector<int> path)
    {
        if(!root)
            return false;
        if(!root->left && !root->right)  //current node is leaf node
        {
            currSum=currSum+root->val;
            if(currSum==targetSum)
            {
                path.push_back(root->val);
                res.push_back(path);
                return true;
            }
            return false;
        }
        currSum=currSum+root->val;
        path.push_back(root->val);
        bool l = dfs(root->left,currSum,targetSum,res,path);
        bool r = dfs(root->right,currSum,targetSum,res,path);
        return(l || r);
    }
};
```

## Complexity
- Time - O(n)
- Space - O(n)


## Ideal Code

```cpp
class Solution {
public:
    vector<vector<int>> pathSum(TreeNode* root, int sum) {
        vector<vector<int> > paths;
        vector<int> path;
        findPaths(root, sum, path, paths);
        return paths;  
    }
private:
    void findPaths(TreeNode* node, int sum, vector<int>& path, vector<vector<int> >& paths) {
        if (!node) 
	        return;
        path.push_back(node -> val);
        if (!(node -> left) && !(node -> right) && sum == node -> val)
            paths.push_back(path);
        findPaths(node -> left, sum - node -> val, path, paths);
        findPaths(node -> right, sum - node -> val, path, paths);
        path.pop_back();
    }
};
```

## Complexity
- Time - O(n)
- Space - O(n)


## My Notes
- practice such problems

### Tags
#medium #BinaryTree #DepthFirstSearch 