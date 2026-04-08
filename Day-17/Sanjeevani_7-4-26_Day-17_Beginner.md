# POTD Day 17 : Implement Stack using Queues

### Description
Implement a last-in-first-out (LIFO) stack using only standard queue operations (`push to back`, `peek/pop from front`, `size`, and `is empty`). The stack should support `push`, `pop`, `top`, and `empty`.

### Approach
I used a **Single Queue** approach to simulate the stack behavior efficiently.
- **Push Operation:**
  - When a new element `x` is added, I first push it to the back of the queue as usual.
  - To make it behave like a stack (where the last element added is at the front), I rotate the queue. I take all previous elements (size - 1) and move them one by one from the front to the back.
  - This ensures that the newly added element is now at the front of the queue, making `pop` and `top` operations $O(1)$.
- **Pop/Top Operation:** Since the last pushed element is always at the front after the rotation, these operations are simply standard queue front operations.
- **Empty Operation:** Simply checks if the queue is empty.

### Complexity
**Time:**
- `push`: $O(n)$ — Each push requires rotating the entire queue.
- `pop`/`top`: $O(1)$ — The element is already at the front.
- `empty`: $O(1)$.
**Space: $O(n)$** — We use a single queue to store all $n$ elements.

### Code
```cpp
class MyStack {
private:
    queue<int> q;

public:
    MyStack() {}
    
    void push(int x) {
        q.push(x);
        int s = q.size();
        // Rotate the queue to bring the new element to the front
        for (int i = 0; i < s - 1; i++) {
            q.push(q.front());
            q.pop();
        }
    }
    
    int pop() {
        int topElement = q.front();
        q.pop();
        return topElement;
    }
    
    int top() {
        return q.front();
    }
    
    bool empty() {
        return q.empty();
    }
};
```

### ScreenShot
<img width="979" height="546" alt="image" src="https://github.com/user-attachments/assets/c2d4aa35-45c9-437c-bc0a-bd545bfe790e" />
