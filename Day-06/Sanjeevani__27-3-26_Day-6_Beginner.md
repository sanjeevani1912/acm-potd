# POTD Day 6 : Check If N and Its Double Exist

### Description
Given an array `arr` of integers, check if there exist two indices `i` and `j` such that `i != j`, `0 <= i, j < arr.length`, and `arr[i] == 2 * arr[j]`.

### Approach
I used a **Hash Set (unordered_set)** to solve this problem in a single pass.
- I iterated through the array, and for each element `num`, I checked two conditions:
  1. Does `2 * num` already exist in the set?
  2. Is `num` even, and does `num / 2` already exist in the set?
- If either condition is met, it means we have found a pair that satisfies the requirement, and I returned `true`.
- If the current element didn't have a match, I added it to the set and continued.
- This approach is efficient because set lookups are $O(1)$ on average.

### Complexity
**Time: $O(n)$** — We traverse the array exactly once, performing constant-time lookups.  
**Space: $O(n)$** — In the worst case, we store all elements of the array in the hash set.

### Code
```cpp
class Solution {
public:
    bool checkIfExist(vector<int>& arr) {
        unordered_set<int> seen;
        
        for (int num : arr) {
            // Check if double exists OR if half exists (only if even)
            if (seen.count(2 * num) || (num % 2 == 0 && seen.count(num / 2))) {
                return true;
            }
            // Add current number to the set
            seen.insert(num);
        }
        
        return false;
    }
};
```

### Screenshot
<img width="1072" height="544" alt="image" src="https://github.com/user-attachments/assets/a175e7d8-d46d-4095-b040-0d5b0de4892b" />

