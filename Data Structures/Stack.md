---
aliases:
  - Monotonic Stack
tags:
  - datastructure
---

A Stack is a linear data structure that follows the **LIFO (Last-In-First-Out)** principle.
Stack can be defined as a container in which insertion and deletion can be done from the one end known as the top of the stack.

**Fun Fact:** Stacks are used in implementing backtracking and function calls

## Time Complexity:
* Push: $O(1)$
* Pop: $O(1)$

# Monotonic Stack

A monotonic stack is a stack whose elements are monotonically increasing or decreasing.

There can be four types of monotonic stacks.
* **Strictly increasing** $(\geq)$
* **Non-decreasing** $(>)$
* **Strictly decreasing** $(\leq)$
* **Non-increasing** $(<)$
## When to Use Monotonic Stack
* It is used for solving questions of the type *(next/previous) (greater/smaller) element*
> The element that pops the top element of stack has to be the "next greatest/smallest".

**Food for thought:** Can we maintain both previous and next greater element in the sequence at once? How?

* Monotonic Stack is the best time complexity solution for many “_range queries in an array”_ problems.
> Given an array of numbers, the array range query problem is to build a data structure that can efficiently answer queries of a particular type mentioned in terms of an interval of the indices.

* Monotonic stack helps us maintain maximum and and minimum elements in the range and keeps the order of elements in the range. 
> Think top and bottom elements of monotonic stack.


## Code Example for Monotonic Stack
```rust
fn find_next_and_previous_greater_indexes(arr: Vec<i32>) -> (Vec<i32>, Vec<i32>) {
    let mut stack: Vec<usize>  = Vec::new();
    // Comment out one of the two below according to the need
    let mut next_greater: Vec<i32> = vec![-1; arr.len()];
    let mut prev_greater: Vec<i32> = vec![-1; arr.len()];
    for (i, &val) in arr.iter().enumerate() {
        while let Some(&index) = stack.last() {
            if arr[index] <= val {
                stack.pop();
                next_greater[index] = arr[i]; // comment out if you dont want to find next greater.
                continue;
            }
            break;
        }
        
        // Comment out if you dont want to find previous greater
        if let Some(&index) = stack.last() {
            prev_greater[i] = arr[index];
        }
        
        stack.push(i);
    }
    (prev_greater, next_greater)
}
```