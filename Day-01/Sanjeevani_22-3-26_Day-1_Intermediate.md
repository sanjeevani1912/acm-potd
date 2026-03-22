# POTD Day 1 : 3Sum

### Description
Given an integer array nums, return all unique triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and their sum equals zero. The solution set must not contain duplicate triplets.

### Approach
I used the **Sorting + Two-Pointer technique**. 
- First, I sorted the array to easily handle duplicates and use the two-pointer logic.
- I iterated through the array with a fixed pointer `i`.
- For each `i`, I placed a `left` pointer at `i + 1` and a `right` pointer at the end of the array.
- Based on the sum, I moved the pointers inward, skipping identical values to ensure the triplets in the result are unique.

### Complexity
- **Time: $O(n^2)$** — Since we use a nested loop structure (one for the fixed element and two-pointers for the rest).
- **Space: $O(1)$** — We are only using a few pointers and modifying the existing array.

### Code
```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> result;
        sort(nums.begin(), nums.end());
        
        for (int i = 0; i < nums.size(); i++) {
            if (i > 0 && nums[i] == nums[i-1]) continue;
            
            int left = i + 1;
            int right = nums.size() - 1;
            
            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                
                if (sum == 0) {
                    result.push_back({nums[i], nums[left], nums[right]});
                    while (left < right && nums[left] == nums[left + 1]) left++;
                    while (left < right && nums[right] == nums[right - 1]) right--;
                    left++;
                    right--;
                } else if (sum < 0) {
                    left++;
                } else {
                    right--;
                }
            }
        }
        return result;
    }
};
```

### Screenshot
<img width="1089" height="551" alt="image" src="https://github.com/user-attachments/assets/a2754d53-a527-4d91-b291-26319431b062" />

