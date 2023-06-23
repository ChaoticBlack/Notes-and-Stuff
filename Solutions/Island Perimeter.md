You are given `row x col` `grid` representing a map where `grid[i][j] = 1` represents land and `grid[i][j] = 0` represents water.

Grid cells are connected **horizontally/vertically** (not diagonally). The `grid` is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells).

The island doesn't have "lakes", meaning the water inside isn't connected to the water around the island. One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.

## Solution

## My Code

```cpp
class Solution {
public:
    int islandPerimeter(vector<vector<int>>& grid) {
        int res = 0;
        int m = grid.size(), n = grid[0].size();
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                if(grid[i][j] == 1){
                    //Unconnected cell
                    res += 4;
                    //check connection to the left
                    if(j > 0 && grid[i][j - 1] == 1) 
                        res -= 1;
                    //check connection up
                    if(i > 0 && grid[i-1][j] == 1) 
                        res -= 1;
                    //check connection to the right
                    if(j < n - 1 && grid[i][j + 1] == 1) 
                        res -= 1;
                    //check bottom connection
                    if(i < m - 1 && grid[i+1][j] == 1) 
                        res -= 1;
                }
            }
        }
        return res;
    }
};
```

## Complexity
- Time - O(n)
- Space - O(1)


## Ideal Code
same as above
## Complexity
- Time - O(n)
- Space - O(1)


## My Notes
Easy if else if else question. Just revise what the optimal way to write the if else conditions is.

### Tags
#easy #2DMatrix 