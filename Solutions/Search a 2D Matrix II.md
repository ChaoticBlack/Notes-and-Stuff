Write an efficient algorithm that searches for a value `target` in an `m x n` integer matrix `matrix`. This matrix has the following properties:

- Integers in each row are sorted in ascending from left to right.
- Integers in each column are sorted in ascending from top to bottom.

## Solution
```audio-player
[[Search a 2D Matrix II.mp3]]
```

## My Code

```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int x = 0;
        int y = matrix[0].size()-1;

        while(y>=0 && x<matrix.size())
        {
            if(matrix[x][y]==target)
                return true;
            if(matrix[x][y]>target)
            {
                y--;
            }
            else if(matrix[x][y]<target)
            {
                x++;
            }
        }
        return false;

    }
};
```

## Complexity
- Time - O(m + n)
- Space - O(1)


## Ideal Code
my code is ideal

## Complexity
- Time - O(m + n)
- Space - O(1)


## My Notes
kinda sexy ngl.

### Tags
#medium #BinarySearch #DivideandConquer #2DMatrix 