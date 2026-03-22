# POTD Day 1 : Remove Duplicates from Sorted Array

### Description
Given a sorted array, remove duplicates in-place such that each unique element appears only once. The relative order should be kept the same, and the function should return the number of unique elements.

### Approach
I used the **Two-Pointer technique**. 
- I maintained a pointer `j` to track the position of the last unique element.
- I iterated through the array with a pointer `i`.
- Whenever `nums[i]` differed from `nums[j]`, I incremented `j` and updated `nums[j]` to `nums[i]`.
- This ensures all unique elements are moved to the front in $O(n)$ time complexity and $O(1)$ space complexity.

### Complexity
**Time: $O(n)$** — because we only loop through the array once.  
**Space: $O(1)$** — we didn't create any new arrays, just modified the one given.

### Code
```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.empty()) return 0;
        int j = 0;
        for (int i = 1; i < nums.size(); i++) {
            if (nums[i] != nums[j]) {
                j++;
                nums[j] = nums[i];
            }
        }
        return j + 1;
    }
};
```

### Screenshot
<img width="880" height="521" alt="image" src="https://github.com/user-attachments/assets/f390ff16-2c6e-4330-9162-f2b04c965ae5" />
