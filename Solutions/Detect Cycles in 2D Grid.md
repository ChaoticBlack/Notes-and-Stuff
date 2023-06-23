Given a 2D array of characters `grid` of size `m x n`, you need to find if there exists any cycle consisting of the **same value** in `grid`.

A cycle is a path of **length 4 or more** in the grid that starts and ends at the same cell. From a given cell, you can move to one of the cells adjacent to it - in one of the four directions (up, down, left, or right), if it has the **same value** of the current cell.

Also, you cannot move to the cell that you visited in your last move. For example, the cycle `(1, 1) -> (1, 2) -> (1, 1)` is invalid because from `(1, 2)` we visited `(1, 1)` which was the last visited cell.

Return `true` if any cycle of the same value exists in `grid`, otherwise, return `false`.

## Solution
```audio-player
[[Detect Cycles in 2D Grid.mp3]]
```

## My Code

```cpp
class Solution {
public:
    bool containsCycle(vector<vector<char>>& grid) {
        int m = grid.size();
        int n = grid[0].size();
        vector<vector<int>> visited(m, vector<int>(n, 0));
        int len = 1;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (dfs(grid, visited, i, j, i, j, len))
                    return true;
            }
        }
        return false;
    }

    bool dfs(vector<vector<char>>& grid, vector<vector<int>>& visited, int i, int j, int prevI, int prevJ, int len) {
        if (visited[i][j] == 1) {
            if (len >= 4)
                return true;
            return false;
        }
        visited[i][j] = 1;
        bool u = false;
        bool d = false;
        bool l = false;
        bool r = false;
        if (i - 1 >= 0 && grid[i - 1][j] == grid[i][j] && (i - 1 != prevI || j != prevJ))
            u = dfs(grid, visited, i - 1, j, i, j, len + 1);

        if (i + 1 < grid.size() && grid[i + 1][j] == grid[i][j] && (i + 1 != prevI || j != prevJ))
            d = dfs(grid, visited, i + 1, j, i, j, len + 1);

        if (j - 1 >= 0 && grid[i][j - 1] == grid[i][j] && (i != prevI || j - 1 != prevJ))
            l = dfs(grid, visited, i, j - 1, i, j, len + 1);

        if (j + 1 < grid[0].size() && grid[i][j + 1] == grid[i][j] && (i != prevI || j + 1 != prevJ))
            r = dfs(grid, visited, i, j + 1, i, j, len + 1);

        return u || d || l || r;
    }
};
```

## Complexity
- Time - O(m*n)
- Space - O(m*n)


## Ideal Code
same as above just cleaner.

## My Notes
Good question, revise well.

### Tags
#medium #2DMatrix #DepthFirstSearch #BreadthFirstSearch 