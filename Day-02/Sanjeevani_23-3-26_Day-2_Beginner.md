# POTD Day 2 : Two Sum

### Description
Given an array of integers `nums` and an integer `target`, return the indices of the two numbers such that they add up to the target. Each input has exactly one solution, and the same element cannot be used twice.

### Approach
I used a **Hash Map (One-Pass)** approach to solve this efficiently.
- I iterated through the array while storing each number's value and its index in a map.
- For every number `nums[i]`, I calculated its complement: `complement = target - nums[i]`.
- I checked if this complement already existed in the map.
- If it existed, I found the two indices and returned them immediately. 
- This avoids the $O(n^2)$ brute force approach by using extra space to reduce time complexity.

### Complexity
**Time: $O(n)$** — We traverse the list only once, and each lookup in the hash map takes $O(1)$ on average.  
**Space: $O(n)$** — In the worst case, we store almost all elements of the array in the map.

### Code
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> numMap;
        
        for (int i = 0; i < nums.size(); i++) {
            int complement = target - nums[i];
            
            // Check if complement exists in map
            if (numMap.find(complement) != numMap.end()) {
                return {numMap[complement], i};
            }
            
            // Otherwise, add current number to map
            numMap[nums[i]] = i;
        }
        return {}; // Should not reach here per constraints
    }
};
```

### Screenshot
<img width="930" height="554" alt="image" src="https://github.com/user-attachments/assets/f2e5418d-0a1d-4879-bc57-934c857c146e" />
