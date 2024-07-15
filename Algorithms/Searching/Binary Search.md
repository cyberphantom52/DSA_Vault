---
tags: algorithm, searching
aliases: Half-Interval Search
---
Binary search is an efficient searching algorithm used to find the position of a specific value within a sorted sequence. It works by repeatedly dividing the search space in half until the target value is found or the search space becomes empty. It's a [[Divide And Conquer]] algorithm.

#### Time Complexity: $O(log(n))$

#### Space Complexity: $O(1)$

#### Tips
- Can be used to find lower/upper bound in an array.
- Binary search can be applied to answer space.

#### Questions to try
##### For 1-D Arrays
1. [Implement Lower Bound](https://www.geeksforgeeks.org/problems/floor-in-a-sorted-array-1587115620/1)
2. [Implement Upper Bound](https://www.geeksforgeeks.org/problems/ceil-the-floor2802/1)
3. [Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)
4. [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
5. [Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/)
7. [Find Peak Element](https://leetcode.com/problems/find-peak-element/description/)
##### For Answer Space
1. [Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/)
2. [Kth Missing Positive Number](https://leetcode.com/problems/kth-missing-positive-number/)
3. [Book Allocation](https://www.naukri.com/code360/problems/allocate-books_1090540)
4. [Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/)
5. [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)
6. [K-th element of two Arrays](https://www.geeksforgeeks.org/problems/k-th-element-of-two-sorted-array1317/1)
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