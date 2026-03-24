# POTD Day 3 : Best Time to Buy and Sell Stock

### Description
Given an array `prices` where `prices[i]` is the price of a stock on the $i^{th}$ day, find the maximum profit possible by buying on one day and selling on a different day in the future. If no profit can be made, return 0.

### Approach
I used a **Single Pass (Greedy)** approach to solve this in linear time.
- I maintained a variable `min_price` to track the lowest price encountered so far.
- As I iterated through the array, I calculated the potential profit if I sold at the current price (`current_price - min_price`).
- I updated the `max_profit` whenever I found a higher value.
- This ensures we always buy at the lowest point seen so far and sell at the highest possible point after that purchase.

### Complexity
**Time: $O(n)$** — We traverse the prices array exactly once.  
**Space: $O(1)$** — We only use two variables (`min_price` and `max_profit`) regardless of input size.

### Code
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int min_price = INT_MAX;
        int max_profit = 0;
        
        for (int price : prices) {
            // Update min_price if current price is lower
            if (price < min_price) {
                min_price = price;
            } 
            // Calculate profit and update max_profit if it's better
            else if (price - min_price > max_profit) {
                max_profit = price - min_price;
            }
        }
        
        return max_profit;
    }
};
```

### Screenshot
<img width="995" height="550" alt="image" src="https://github.com/user-attachments/assets/1fd44660-5db7-47a7-b097-47ccd2fb693c" />
