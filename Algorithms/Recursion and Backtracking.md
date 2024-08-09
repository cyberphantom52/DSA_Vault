
// WIP
```rust
impl Solution {
    fn helper(nums: &Vec<i32>, index: usize, mut subset: Vec<i32>) -> Vec<Vec<i32>> {
	    // if index exceeds length of array, return the subset that has been generated
        if index == nums.len() {
            return vec![subset];
        }
        
        // Case 1: Consider the current element for the subset
        subset.push(nums[index]);
        let take = Solution::helper(nums, index + 1, subset.clone());

		// Case 2: Don't consider the current element for the subset
        subset.pop();
        let not_take = Solution::helper(nums, index + 1, subset);

		// Join the take and not_take case to get all combinations
        [take, not_take].concat().to_vec()
    }

    pub fn subsets(nums: Vec<i32>) -> Vec<Vec<i32>> {
        Solution::helper(&nums, 0, Vec::new())
    }
}
```