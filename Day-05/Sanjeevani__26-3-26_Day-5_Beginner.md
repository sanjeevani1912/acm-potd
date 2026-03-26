# POTD Day 5 : Move Zeroes

### Description
Given an integer array `nums`, move all 0's to the end of it while maintaining the relative order of the non-zero elements. This must be done in-place without making a copy of the array.

### Approach
I used the **Two-Pointer technique** to solve this problem efficiently in a single pass.
- I maintained a pointer `lastNonZeroFoundAt` (let's call it `i`) to keep track of the position where the next non-zero element should be placed.
- I iterated through the array with another pointer `j`.
- Whenever `nums[j]` was non-zero, I swapped `nums[i]` and `nums[j]` and incremented `i`.
- By swapping instead of just overwriting, the zeroes are naturally pushed to the end of the array while the relative order of non-zero elements is preserved.

### Complexity
**Time: $O(n)$** — We traverse the array exactly once.  
**Space: $O(1)$** — We perform the operations in-place using only two integer pointers.

### Code
```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int lastNonZeroFoundAt = 0;
        
        for (int j = 0; j < nums.size(); j++) {
            if (nums[j] != 0) {
                // Swap current non-zero element with the element at the last non-zero pointer
                swap(nums[lastNonZeroFoundAt], nums[j]);
                lastNonZeroFoundAt++;
            }
        }
    }
};
```

### Screenshot
<img width="927" height="559" alt="image" src="https://github.com/user-attachments/assets/aa0a0ca3-4a80-4b8b-8cb3-b9a824fa79cd" />
