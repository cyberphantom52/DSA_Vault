---
tags:
  - algorithm
  - sorting
---

This is a [[Divide And Conquer]] algorithm just like [[Merge Sort]]. But the primary difference to Merge Sort is that the sorting happens in-place. So, from that perspective, Quick sort is slightly better than Merge sort.

#### Time Complexity
- **Best case:** When pivot moves to middle of array. $O(n*log(n))$
- **Average Case:** $O(n*log(n))$
- **Worst  Case:** Pivot is first or last element. i.e Array is almost sorted. $O(n^2)$
#### Space Complexity: $O(log(n))$
#### Working
- Choose an element to be the pivot (Its better to choose element at random but for simplicity we can always choose the first or last element as pivot) And move it to its correct place. The correct index of the pivot element divides the array into two sub arrays. This is done by the `partition` function.
- Recursively call `quick_sort` on the sub arrays until the entire array is sorted.

#### Tips
- It's can be used to separate the **Kth smallest** or **largest elements**.
#### Code Example
```rust
pub fn partition(input: &mut Vec<i32>, start: usize, end: usize) -> usize {
    let pivot = input[start];
    let mut index = start;
    (start..end).for_each(|i| {
        if input[i] < pivot {
            index += 1;
            input.swap(index, i);
        }
    });
    input.swap(start, index);
    index
}
```

```rust
pub fn quick_sort(input: &mut Vec<i32>, start: usize, end: usize) {
    if start < end {
        let pivot = partition(input, start, end);
        quick_sort(input, start, pivot);
        quick_sort(input, pivot + 1, end);
    }
}
```