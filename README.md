# LeetCode 155 - Min Stack

## Problem Statement
Design a stack that supports the following operations in constant time:

- `push(x)` – Push element x onto stack.
- `pop()` – Removes the element on top of the stack.
- `top()` – Get the top element.
- `getMin()` – Retrieve the minimum element in the stack.

All operations must run in **O(1)** time complexity.

## Approach

Use two stacks:

1. **Main Stack (`st`)**
   - Stores all elements.

2. **Minimum Stack (`minSt`)**
   - Stores the minimum elements encountered so far.

### Push Operation
- Push the value into the main stack.
- If the minimum stack is empty or the new value is less than or equal to the current minimum, push it into the minimum stack.

### Pop Operation
- If the top element of the main stack equals the top element of the minimum stack, remove it from both stacks.
- Pop the element from the main stack.

### Top Operation
- Return the top element of the main stack.

### Get Minimum Operation
- Return the top element of the minimum stack.

## C++ Solution

```cpp
class MinStack {
public:
    stack<int> st;
    stack<int> minSt;

    MinStack() {
    }

    void push(int val) {
        st.push(val);

        if(minSt.empty() || val <= minSt.top()) {
            minSt.push(val);
        }
    }

    void pop() {
        if(st.top() == minSt.top()) {
            minSt.pop();
        }

        st.pop();
    }

    int top() {
        return st.top();
    }

    int getMin() {
        return minSt.top();
    }
};
