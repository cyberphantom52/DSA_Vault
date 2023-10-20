---
tag: algorithm
---
Kadane's algorithm is a [[dynamic programming]] approach used to solve the maximum sub-array problem, which involves finding the contiguous sub-array with the maximum sum in a sqeuence of numbers. The algorithm was proposed by Jay Kadane in 1984 and has a time complexity of $O(n)$.

## Working of Kadane's Algorithm:
The algorithm works by iterating over the array and keeping track of the maximum sum of the sub-array ending at each position. 
At each position $i$, we have two options:
- Either add the element at position $i$ to the current maximum sub-array.
- Start a new sub-array at position $i$. 
The maximum of these two options is the maximum sub-array ending at position $i$.

## Code Example
```rust
pub fn max_sub_array(nums: Vec<i32>) -> i32 {
    let (mut global_max, mut local_max) = (nums[0], nums[0]);
    let size = nums.len();

    for i in 1..size {
        local_max = i32::max(nums[i], local_max + nums[i]);
        global_max = i32::max(global_max, local_max);
    }
    global_max
}
```

## Advantages:
- **Efficiency:** Kadane's Algorithm has a time complexity of $O(n)$, which  makes it a great solution for large datasets.
- **Simplicity:** Easy to understand and implement compared to other algorithms such as the [[Divide And Conquer]] algorithm.
- **Space Complexity:**  $O(1)$
- **Dynamic Programming:** Kadane's Algorithm is a classic example of [[dynamic programming]], a technique that breaks down a problem into smaller sub problems and stores the solutions to these sub problems to avoid redundant computation.

## Disadvantages:

- Only finds sum and not the sub-array itself:
- **Does not handle negative numbers well:** If an input array has only negative numbers, the algorithm will return the maximum negative number instead of 0. This can be overcome by adding an additional step to the algorithm to check if the array has only negative numbers.
- Not suitable for non-contiguous sub-arrays.