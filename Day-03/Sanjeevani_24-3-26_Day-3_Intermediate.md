# POTD Day 3 : Sort Colors

### Description
Given an array `nums` with $n$ objects colored red (0), white (1), or blue (2), sort them in-place so that objects of the same color are adjacent in the order 0, 1, and 2. This must be done without using the library's sort function.

### Approach
I implemented the **Dutch National Flag algorithm** (3-way partitioning) to solve this in a single pass.
- I used three pointers: `low`, `mid`, and `high`.
- `low` tracks the boundary for 0s, `mid` explores the array, and `high` tracks the boundary for 2s.
- If `nums[mid]` is 0, I swap it with `nums[low]` and move both pointers forward.
- If `nums[mid]` is 1, I just move the `mid` pointer forward.
- If `nums[mid]` is 2, I swap it with `nums[high]` and move `high` backward (without moving `mid`, as the swapped element needs to be checked).



### Complexity
**Time: $O(n)$** — We traverse the array only once.  
**Space: $O(1)$** — We sort the array in-place using only three pointers.

### Code
```cpp
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int low = 0, mid = 0, high = nums.size() - 1;
        
        while (mid <= high) {
            if (nums[mid] == 0) {
                swap(nums[low], nums[mid]);
                low++;
                mid++;
            } 
            else if (nums[mid] == 1) {
                mid++;
            } 
            else { // nums[mid] == 2
                swap(nums[mid], nums[high]);
                high--;
            }
        }
    }
};
```

### Screenshot
<img width="893" height="541" alt="image" src="https://github.com/user-attachments/assets/f372dee5-b308-45bb-bc93-b8e5cc0efe67" />


