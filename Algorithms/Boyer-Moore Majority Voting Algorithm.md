---
tags: algorithm
---
The Boyer-Moore voting algorithm is used to find the majority element among the given elements that have more than $N/2$ occurrences.

#### Time Complexity: $O(N)$
#### Space Complexity: $O(1)$

## Working:
This [[algorithm]] processes each element one at a time. Choose a candidate from the given set of elements. If it is same as the candidate element, increase the votes. Otherwise decrease the votes. If votes become 0, take another new element as the new candidate.

## Code Example:
```rust
pub fn majority_element(nums: Vec<i32>) -> i32 {
    let (mut candidate, mut count) = (0, 0);
    for &num in &nums {
        if count == 0 {
            candidate = num;
        }

		if num == candidate {
			count += 1;
		} else {
			count -= 1;
		}
    }
    candidate
}
```

#### Alternate Version:
```rust
pub fn majority_element(nums: Vec<i32>) -> i32 {
    let (candidate, _) = nums.iter().fold((0, 0), |(c, v), &x|{
        if v == 0 {
            (x, 1)
        } else if c == x {
            (c, v + 1)
        } else {
            (c , v - 1)
        }
    });
    candidate
}
```
