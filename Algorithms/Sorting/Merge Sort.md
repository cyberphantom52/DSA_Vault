---
tags: algorithm, sorting
---
Merge Sort is a [[Divide And Conquer]] algorithm that works by recursively breaking down a problem into two or more sub-problems of the same or related type, until these become simple enough to be solved directly. The solutions to the sub-problems are then combined to give a solution to the original problem. So Merge Sort first divides the array into equal halves and then combines them in a sorted 
manner.

#### Time Complexity:
- **Best case:** Elements sorted in ascending order. $O(n*log(n))$
- **Average Case:** $O(n*log(n))$
- **Worst  Case:** Elements sorted in descending order.$O(n*log(n))$

#### Space Complexity: $O(n)$

## Working:
- **Divide:** Keep dividing the problem into smaller sub problems until it's no longer divisible, a list with single item is always considered sorted.
- **Conquer:** Start combining the solutions of sub problems recursively.

A `merge_sort` function ultimately has two functions inside of it:
1. A `merge_sort` function, which will continue to split the input array recursively, and will also call `merge`. (Divide Step)
2. A `merge` function, merges two sorted lists into a single sorted list. (Conquer Step)

## Advantage:
- Stable Sorting
- Suitable for [[Linked List]]. Because it doesn't require random access.

## Disadvantage:
- Additional memory usage as not in place.
- Slow for smaller arrays.

## Code Example
```rust
pub fn merge(left: &mut Vec<i32>, mut right: Vec<i32>) {
    let (mut m, mut n) = (left.len(), right.len());
    
    let mut index = m + n;
    left.resize(index, 0);
    
    while index > 0 && n > 0 {
        if m > 0 && left[m - 1] > right[n - 1] {
            left.swap(index - 1, m - 1);
            m -=  1;
        } else {
            std::mem::swap(&mut left[index - 1], &mut right[n - 1]);
            n -= 1;
        }
        index -= 1;
    }
}

fn merge_sort(mut input: Vec<i32>) -> Vec<i32> {
    if input.len() == 1 {
        return input;
    }

    let mid = input.len() / 2;
    let mut left = merge_sort(input.drain(..mid).collect());
    let right = merge_sort(input);
    merge(&mut left, right);
    left
}
```
