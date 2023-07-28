---
tag: algorithm
aliases: Dutch Flag Algorithm, Three-Way Partitioning
---
The Dutch National Flag algorithm, also known as the Dutch Flag Partitioning or Three-Way Partitioning, is a sorting algorithm designed to efficiently sort an [[array]] containing three distinct elements or values. It's a type of unstable sorting algorithm i.e relative order of equal elements might not be preserved. It is often used as a subroutine in other sorting algorithms like [[Quick Sort]] and [[Merge Sort]] to handle duplicate keys or multiple values.

#### Time Complexity: $O(N)$

#### Space Complexity: $O(1)$

## Code Example:
```rust
pub fn dnf(nums: &mut Vec<i32>) {
    let (mut low, mut mid, mut high) = (0, 0, nums.len() - 1);

    while mid <= high && high != 0 {
        match nums[mid] {
            0 => {
                nums.swap(mid ,low);
                low += 1;
                mid += 1;
            },
            2 => {
                nums.swap(mid ,high);
                high -= 1;
            },
            _ => {
                mid += 1;
            }
        }
    }
}
```
