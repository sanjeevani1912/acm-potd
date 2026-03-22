# POTD Day 1 : Trapping Rain Water

### Description
Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

### Approach
I used the **Optimized Two-Pointer technique**. 
- I placed two pointers, `left` at the start and `right` at the end of the array.
- I tracked the maximum height seen so far from both the left (`left_max`) and the right (`right_max`).
- Since the water trapped at any bar is limited by the shorter of the two sides, I moved the pointer with the smaller height.
- This allowed me to calculate the trapped water at each step without needing extra arrays for prefix/suffix maximums.

### Complexity
**Time: $O(n)$** — We traverse the array only once using the two pointers.  
**Space: $O(1)$** — We only use a constant amount of extra space for variables.

### Code
```cpp
class Solution {
public:
    int trap(vector<int>& height) {
        int n = height.size();
        if (n <= 2) return 0;
        
        int left = 0, right = n - 1;
        int left_max = 0, right_max = 0;
        int water = 0;
        
        while (left < right) {
            if (height[left] < height[right]) {
                if (height[left] >= left_max) {
                    left_max = height[left];
                } else {
                    water += left_max - height[left];
                }
                left++;
            } else {
                if (height[right] >= right_max) {
                    right_max = height[right];
                } else {
                    water += right_max - height[right];
                }
                right--;
            }
        }
        return water;
    }
};
```

### Screenshot
<img width="906" height="587" alt="image" src="https://github.com/user-attachments/assets/88d3c5f6-259c-4e7b-8722-3d8ef356128f" />
