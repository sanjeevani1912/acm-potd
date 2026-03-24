# POTD Day 3 : Largest Rectangle in Histogram

### Description
Given an array of integers `heights` representing the histogram's bar heights where the width of each bar is 1, return the area of the largest rectangle in the histogram.

### Approach
I used a **Monotonic Increasing Stack** to solve this problem in linear time.
- The goal is to find, for each bar, the nearest smaller bar to its left and its right. These boundaries define the maximum width of a rectangle using the current bar as the shortest height.
- I iterated through the heights, pushing the index onto the stack if the current height was greater than the height at the stack's top.
- When I encountered a shorter bar, I popped from the stack. The popped bar's height is the height of the rectangle, and the width is determined by the current index and the new top of the stack.
- To handle the remaining bars in the stack after the loop, I used a dummy height of 0 at the end.

### Complexity
**Time: $O(n)$** — Each bar is pushed onto and popped from the stack exactly once.  
**Space: $O(n)$** — In the worst case, the stack can store all the indices of the bars.

### Code
```cpp
class Solution {
public:
    int largestRectangleArea(vector<int>& heights) {
        int n = heights.size();
        stack<int> st;
        int max_area = 0;
        
        for (int i = 0; i <= n; i++) {
            // Use 0 as a sentinel value for the end of the histogram
            int current_height = (i == n) ? 0 : heights[i];
            
            while (!st.empty() && heights[st.top()] >= current_height) {
                int height = heights[st.top()];
                st.pop();
                
                // Calculate width
                int width = st.empty() ? i : (i - st.top() - 1);
                max_area = max(max_area, height * width);
            }
            st.push(i);
        }
        
        return max_area;
    }
};
```

### Screenshot
<img width="1038" height="540" alt="image" src="https://github.com/user-attachments/assets/113c49bf-92ed-450a-830c-0678af8721eb" />
