You are given an `m x n` binary matrix `grid`. An island is a group of `1`'s (representing land) connected **4-directionally** (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.

The **area** of an island is the number of cells with a value `1` in the island.

Return _the maximum **area** of an island in_ `grid`. If there is no island, return `0`.

## Solution
```audio-player
[[Max Area of Island.mp3]]
```

## My Code

```cpp
class Solution {
public:
    int maxAreaOfIsland(vector<vector<int>>& grid) {
        int m=grid.size();
        int n=grid[0].size();
        vector<vector<int>> visited(m, vector<int>(n,0));
        int ans=0;
        for(int i=0;i<m;i++)
        {
            for(int j=0;j<n;j++)
            {
                if(grid[i][j]==1 && visited[i][j]==0)
                    ans=max(ans,dfs(grid,visited,i,j));
            }
        }
        return ans;
    }

    int dfs(vector<vector<int>>& grid, vector<vector<int>>& visited, int i, int j)
    {
        if(i<0 || j<0 || i>=grid.size() || j>=grid[0].size()|| grid[i][j]!=1 || visited[i][j]==1 )
            return 0;
        int m=grid.size();
        int n=grid[0].size();
        visited[i][j]=1;
        int l = dfs(grid,visited,i,j-1);
        int r = dfs(grid,visited,i,j+1);
        int u = dfs(grid,visited,i-1,j);
        int d = dfs(grid,visited,i+1,j);
        return l+r+u+d+1;
    }
};
```

## Complexity
- Time - O(m*n)
- Space - O(m*n)


## Ideal Code
same as above

## My Notes


### Tags
#medium #2DMatrix #DepthFirstSearch #BreadthFirstSearch 