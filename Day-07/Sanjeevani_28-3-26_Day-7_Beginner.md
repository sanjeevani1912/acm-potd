# POTD Day 7 : Rotate Array

### Description
Given an integer array `nums`, rotate the array to the right by `k` steps, where `k` is non-negative. The rotation should be done in-place.

### Approach
I used the **Three-Step Reversal** algorithm to achieve an in-place rotation in linear time.
- First, I handled cases where `k` is greater than the array size by taking `k = k % n`.
- The rotation can be achieved by three simple reversals:
  1. Reverse the entire array.
  2. Reverse the first `k` elements.
  3. Reverse the remaining `n - k` elements.
- This effectively moves the last `k` elements to the front while maintaining their relative order, all without using any extra auxiliary space.



### Complexity
**Time: $O(n)$** — Each element is visited/swapped a constant number of times across the three reversal steps.  
**Space: $O(1)$** — No extra arrays are created; all swaps are done within the original array.

### Code
```cpp
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        int n = nums.size();
        k = k % n; // Handle cases where k > n
        if (k == 0) return;

        // Step 1: Reverse the whole array
        reverse(nums.begin(), nums.end());
        
        // Step 2: Reverse the first k elements
        reverse(nums.begin(), nums.begin() + k);
        
        // Step 3: Reverse the rest of the elements
        reverse(nums.begin() + k, nums.end());
    }
};
```

### Screenshot
<img width="888" height="551" alt="image" src="https://github.com/user-attachments/assets/61e1866d-a9a5-45f5-ae7f-6cdaa5995cf0" />
