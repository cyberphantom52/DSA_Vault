---
tags: algorithm, searching
aliases: Half-Interval Search
---
Binary search is an efficient searching algorithm used to find the position of a specific value within a sorted sequence. It works by repeatedly dividing the search space in half until the target value is found or the search space becomes empty. It's a [[Divide And Conquer]] algorithm.

#### Time Complexity: $O(log(n))$

#### Space Complexity: $O(1)$

# Code Example

#### Iterative
```rust
fn binary_search(arr: &Vec<i32>, target: i32) -> Option<usize> {
    let mut start = 0;
    let mut end = arr.len() - 1;

    while start <= end {
        let mid = start + (end - start) / 2;

        if arr[mid] == target {
            return Some(mid);
        } else if arr[mid] < target {
            start = mid + 1;
        } else {
            end = mid - 1;
        }
    }

    None
}
```

#### Recursive
```rust
fn binary_search(arr: &Vec<i32>, start: usize, end: usize, target: i32) -> Option<usize> {
	if start >= end {
		return None;
	}

	let mid = start + (end - start) / 2;

	if arr[mid] == target {
		return Some(mid);
	} else if arr[mid] < target {
		return binary_search(arr, mid + 1, end, target);
	} else {
		return binary_search(arr, start, mid, target);
	}
}
```