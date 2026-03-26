# POTD Day 5 : Sliding Window Maximum

### Description
Given an array of integers `nums` and a sliding window of size `k`, return an array containing the maximum value for each window position as it moves from left to right.

### Approach
I used a **Monotonic Decreasing Deque** to solve this problem in linear time.
- I maintained a `deque` that stores indices of elements from the current window.
- The deque is kept in **strictly decreasing order** of values. Before adding a new element, I removed all indices from the back whose values were smaller than or equal to the current element.
- I also removed indices from the front that were no longer within the bounds of the current window (i.e., index < `i - k + 1`).
- The front of the deque always represents the index of the maximum element for the current window.
- Once the first window is fully processed (at index `k-1`), I began adding the front element's value to the result array at each step.



### Complexity
**Time: $O(n)$** — Each element is pushed and popped from the deque at most once.  
**Space: $O(k)$** — The deque stores at most $k$ indices at any given time.

### Code
```cpp
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        deque<int> dq;
        vector<int> result;
        
        for (int i = 0; i < nums.size(); i++) {
            // Remove indices that are out of the current window bound
            if (!dq.empty() && dq.front() == i - k) {
                dq.pop_front();
            }
            
            // Remove elements smaller than current element from back (maintain monotonic decreasing)
            while (!dq.empty() && nums[dq.back()] <= nums[i]) {
                dq.pop_back();
            }
            
            dq.push_back(i);
            
            // Once we have a full window, the front of dq is the maximum
            if (i >= k - 1) {
                result.push_back(nums[dq.front()]);
            }
        }
        
        return result;
    }
};
```

### Screenshot
<img width="1080" height="554" alt="image" src="https://github.com/user-attachments/assets/06b9bd04-317d-4e8f-9b5b-2365287026da" />

