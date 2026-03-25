# POTD Day 4 : Two Sum II - Input Array Is Sorted

### Description
Given a 1-indexed array of integers `numbers` that is already sorted in non-decreasing order, find two numbers such that they add up to a specific target. Return the indices of the two numbers (1-indexed). The solution must use only constant extra space.

### Approach
I used the **Two-Pointer technique**, which is highly efficient for sorted arrays.
- I initialized two pointers: `left` at the beginning of the array (index 0) and `right` at the end of the array (index $n-1$).
- In a loop, I calculated the current sum of the elements at these two pointers.
- If the `current_sum` matched the target, I returned the indices incremented by one (to satisfy the 1-indexed requirement).
- If the `current_sum` was less than the target, I moved the `left` pointer forward to increase the sum.
- If the `current_sum` was greater than the target, I moved the `right` pointer backward to decrease the sum.
- This approach ensures we find the solution in linear time without using extra memory.

### Complexity
**Time: $O(n)$** — We traverse the array at most once with the two pointers.  
**Space: $O(1)$** — We only use two pointer variables regardless of the input size.

### Code
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int left = 0;
        int right = numbers.size() - 1;
        
        while (left < right) {
            int current_sum = numbers[left] + numbers[right];
            
            if (current_sum == target) {
                // Return 1-indexed results
                return {left + 1, right + 1};
            } 
            else if (current_sum < target) {
                left++; // Need a larger sum
            } 
            else {
                right--; // Need a smaller sum
            }
        }
        
        return {}; // Guaranteed exactly one solution
    }
};
```

### Screenshot
<img width="951" height="558" alt="image" src="https://github.com/user-attachments/assets/40017fb6-3890-4ff0-91be-70fa37765fcf" />
