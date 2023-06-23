Given an `m x n` 2D binary grid `grid` which represents a map of `'1'`s (land) and `'0'`s (water), return _the number of islands_.

An **island** is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

## Solution
```audio-player
[[Number of Islands.mp3]]
```

## My Code

```cpp
class Solution {
public:
    int numIslands(vector<vector<char>>& grid) {
        int m=grid.size();
        int n=grid[0].size();
        vector<vector<int>> visited(m, vector<int>(n,0));
        int ans=0;
        for(int i=0;i<m;i++)
        {
            for(int j=0;j<n;j++)
            {
                if(grid[i][j]=='1' && visited[i][j]==0)
                {
                    dfs(grid,visited,i,j);
                    ans=ans+1;
                }
            }
        }
        return ans;
    }

    void dfs(vector<vector<char>>& grid, vector<vector<int>>& visited, int i, int j)
    {
        int m=grid.size();
        int n=grid[0].size();
        if(i<0 || j<0 || i>=grid.size() || j>=grid[0].size()|| grid[i][j]!='1' || visited[i][j]==1 )
            return;
        visited[i][j]=1;
        dfs(grid,visited,i,j-1);
        dfs(grid,visited,i,j+1);
        dfs(grid,visited,i-1,j);
        dfs(grid,visited,i+1,j);
    }
};
```

## Complexity
- Time - O(m*n)
- Space - O(m*n)


## Ideal Code
same as above

## My Notes
Fundamental DFS question. Revise well.

**Be careful to pass the vectors by reference as if passed by value it may lead to Time limit exceeded problem.**

### Tags

#medium #2DMatrix #DepthFirstSearch #BreadthFirstSearch 