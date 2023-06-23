Given a 2D `grid` consists of `0s` (land) and `1s` (water).  An _island_ is a maximal 4-directionally connected group of `0s` and a _closed island_ is an island **totally** (all left, top, right, bottom) surrounded by `1s.`

Return the number of _closed islands_.

## Solution
```audio-player
[[Number of Closed Islands.mp3]]
```

## My Code

```cpp
class Solution {
public:
    int closedIsland(vector<vector<int>>& grid) {
        int m=grid.size();
        int n=grid[0].size();
        vector<vector<int>> visited(m, vector<int>(n,0));
        int ans=0;
        for(int i=1;i<m-1;i++)
        {
            for(int j=1;j<n-1;j++)
            {
                if(grid[i][j]==0 && visited[i][j]==0)
                {
                    if(dfs(grid,visited,i,j))
                        ans=ans+1;
                }
            }
        }
        return ans;
    }

    bool dfs(vector<vector<int>>& grid, vector<vector<int>>& visited, int i, int j)
    {
        int m=grid.size();
        int n=grid[0].size();
        if(i<0 || j<0 || i>=m || j>=n)
            return false;
        if(grid[i][j]==1 || visited[i][j]==1)
            return true;
        visited[i][j]=1;
        bool l = dfs(grid,visited,i,j-1);
        bool r = dfs(grid,visited,i,j+1);
        bool u = dfs(grid,visited,i-1,j);
        bool d = dfs(grid,visited,i+1,j);
        return(l && r && u && d);
    }
};
```

## Complexity
- Time - O(m*n)
- Space - O(m*n)


## Ideal Code
same as above

## My Notes
Revise this question

### Tags
#medium #2DMatrix #DepthFirstSearch #BreadthFirstSearch 
