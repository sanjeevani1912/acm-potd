# POTD Day 16 : Implement Queue using Stacks

### Description
Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue: `push`, `peek`, `pop`, and `empty`.

### Approach
I used two stacks, `input` and `output`, to simulate the FIFO behavior of a queue.
- **Push Operation:** I always push new elements onto the `input` stack. This is an $O(1)$ operation.
- **Pop/Peek Operation:** - Since a stack is LIFO, the oldest element is at the bottom of the `input` stack. 
  - To access it, if the `output` stack is empty, I transfer all elements from `input` to `output`. This reverses their order, placing the oldest element at the top of the `output` stack.
  - I then pop or peek from the `output` stack.
- **Empty Operation:** The queue is only empty if both the `input` and `output` stacks are empty.

### Complexity
**Time:** - `push`: $O(1)$
- `pop`/`peek`: Amortized $O(1)$ — While a single call might take $O(n)$ to transfer elements, each element is moved between stacks at most once across all operations.
- `empty`: $O(1)$  
**Space: $O(n)$** — We store all elements across the two stacks.

### Code
```cpp
class MyQueue {
private:
    stack<int> input, output;

    // Helper function to move elements from input to output
    void shiftStacks() {
        if (output.empty()) {
            while (!input.empty()) {
                output.push(input.top());
                input.pop();
            }
        }
    }

public:
    MyQueue() {}
    
    void push(int x) {
        input.push(x);
    }
    
    int pop() {
        shiftStacks();
        int topElement = output.top();
        output.pop();
        return topElement;
    }
    
    int peek() {
        shiftStacks();
        return output.top();
    }
    
    bool empty() {
        return input.empty() && output.empty();
    }
};
```

### Screenshot
<img width="950" height="564" alt="image" src="https://github.com/user-attachments/assets/eea8f433-ecc2-433c-9f03-3dec00d5a9b6" />

