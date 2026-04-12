# POTD Day 22 : Flood Fill

### Description
Given an $m \times n$ grid representing an image, a starting pixel $(sr, sc)$, and a new color, perform a "flood fill" by changing the color of the starting pixel and all its 4-directionally connected pixels that share the same initial color.

### Approach
I used a **Depth First Search (DFS)** approach to traverse the connected components of the grid.
- First, I stored the `initialColor` of the starting pixel.
- To prevent an infinite recursion loop, I added a check: if the `initialColor` is already equal to the target `color`, I return the image immediately.
- I implemented a recursive function that:
  1. Checks if the current coordinates are within the grid boundaries.
  2. Checks if the current pixel matches the `initialColor`.
  3. Updates the pixel to the new `color`.
  4. Recursively calls itself for the four neighbors (Up, Down, Left, Right).



### Complexity
**Time: $O(N \times M)$** — In the worst case, we visit every pixel in the grid exactly once, where $N$ and $M$ are the dimensions of the image.  
**Space: $O(N \times M)$** — This represents the space used by the recursion stack in the worst-case scenario (e.g., the entire grid needs to be filled).

### Code
```cpp
class Solution {
public:
    void dfs(vector<vector<int>>& image, int r, int c, int initialColor, int newColor) {
        // Boundary checks and color match check
        if (r < 0 || r >= image.size() || c < 0 || c >= image[0].size() || image[r][c] != initialColor) {
            return;
        }

        // Update the current pixel color
        image[r][c] = newColor;

        // Perform DFS in all 4 directions
        dfs(image, r + 1, c, initialColor, newColor); // Down
        dfs(image, r - 1, c, initialColor, newColor); // Up
        dfs(image, r, c + 1, initialColor, newColor); // Right
        dfs(image, r, c - 1, initialColor, newColor); // Left
    }

    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
        int initialColor = image[sr][sc];
        
        // Only perform DFS if the new color is actually different
        if (initialColor != color) {
            dfs(image, sr, sc, initialColor, color);
        }
        
        return image;
    }
};
```

### Screenshot
<img width="961" height="544" alt="image" src="https://github.com/user-attachments/assets/daa79324-26ff-4f82-9f32-db95ea40bb65" />
