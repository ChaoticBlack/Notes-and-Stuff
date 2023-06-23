An image is represented by an `m x n` integer grid `image` where `image[i][j]` represents the pixel value of the image.

You are also given three integers `sr`, `sc`, and `color`. You should perform a **flood fill** on the image starting from the pixel `image[sr][sc]`.

To perform a **flood fill**, consider the starting pixel, plus any pixels connected **4-directionally** to the starting pixel of the same color as the starting pixel, plus any pixels connected **4-directionally** to those pixels (also with the same color), and so on. Replace the color of all of the aforementioned pixels with `color`.

Return _the modified image after performing the flood fill_.

## Solution
```audio-player
[[Flood Fill.mp3]]
```

## My Code

```cpp
class Solution {
public:
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
        int m=image.size();
        int n=image[0].size();
        vector<vector<int>> visited(m, vector<int>(n,0));
        int currColor = image[sr][sc];
        dfs(image,sr,sc,color, currColor,visited);
        return image;

    }
    void dfs(vector<vector<int>>& image, int i, int j, int color, int currColor,vector<vector<int>>& visited)
    {
        if(i<0 || j<0 || i>=image.size()|| j>=image[0].size() || image[i][j]!=currColor ||visited[i][j]==1)
            return;
        image[i][j]=color;
        visited[i][j]=1;
        dfs(image,i,j+1,color, currColor,visited);
        dfs(image,i,j-1,color, currColor,visited);
        dfs(image,i+1,j,color, currColor,visited);
        dfs(image,i-1,j,color, currColor,visited);
    }
};
```

## Complexity
- Time - O(m*n)
- Space - O(m*n)


## Ideal Code
same as above


## My Notes
Even if it seems like visited is not needed for this question it actually is. Listen to audio to understand why.

### Tags
#easy #2DMatrix #DepthFirstSearch #BreadthFirstSearch 
