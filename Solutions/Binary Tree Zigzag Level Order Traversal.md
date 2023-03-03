
Given the root of a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between). 

## Solution
It is similar to the previous problem but the key is figuring out how to get the elements in right to left orer.
for this we use a vector and a flag. We push all the nodes at the current level inside this vector.  If the flag is set reverse the vector (ie traverse from right to left) otherwise normal traversal.

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
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        vector<vector<int>> result;
        queue<TreeNode*> q;
        q.push(root);
        int flag=0;
        while(!q.empty())
        {
            int len = q.size(); // number of nodes at current level
            vector<int> direction;
            for(int i=0;i<len;i++)//so that only nodes at current level are considered and not the newer children nodes that will be added
            {
                TreeNode* node=q.front();
                q.pop();
                if(node!=NULL)  //have to check this because we are pushing left and right children without checking if the are null, easier to check in one place than 2 different places
                {
                    direction.push_back(node->val);
                    q.push(node->left); 
                    q.push(node->right);
                }
            }
            //below if is key
            if (flag%2==1)//forward
            {
                reverse(direction.begin(),direction.end());
            }
            if (direction.size()!=0)
            {
                result.push_back(direction);
            }
            flag++;
        }
        return result;
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

- the mistake that i was makeing is that instead of reversing the vector, i was changing the order in which the nodes were being added to queue (ie if flag was set I was adding right child to queue before left)
- This is stupid, don't do stupid.