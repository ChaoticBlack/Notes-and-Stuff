You are given the `root` of a binary tree containing digits from `0` to `9` only.

Each root-to-leaf path in the tree represents a number.

- For example, the root-to-leaf path `1 -> 2 -> 3` represents the number `123`.

Return _the total sum of all root-to-leaf numbers_. Test cases are generated so that the answer will fit in a **32-bit** integer.

A **leaf** node is a node with no children.

## Solution
```audio-player
[[Sum Root to Leaf Numbers.mp3]]
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
    int sumNumbers(TreeNode* root) {
        int ans=0;
        vector<int> path;
        dfs(root,ans,path);
        return ans;
    }
    void dfs(TreeNode* root, int& ans, vector<int> path)
    {
        //base conditions
        if(!root)
            return;
        path.push_back(root->val);
        if(!root->left && !root->right)
        {
            //calculate sum and add to answer
            long long num=0;
            long long k=1;
            for(int i=path.size()-1;i>=0;i--)
            {
                num=num+k*path[i];
                k=k*10;
            }
            ans=ans+num;
            return;
        }
        dfs(root->left,ans,path);
        dfs(root->right,ans,path);
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
- This problem has the aspect of treating an array as a single number that appears in many other problems. It is noteworthy to remember how to traverse the array and convert it to single number.

### Tags
#medium #BinaryTree #DepthFirstSearch 