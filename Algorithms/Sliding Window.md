The sliding window technique is a method used to solve various algorithmic problems, typically involving arrays or lists. **It is particularly useful for finding sub-arrays that meet certain criteria**, such as maximum sum, average, or a specific property like containing a unique set of elements.
## Example Use cases

- Finding the maximum or minimum sum of a sub-array of fixed size.
- Finding the longest sub-string with unique characters.
- Solving problems involving cumulative sums or averages within a specific range.
- Detecting patterns or anomalies in data streams.

#### Tips:
- In case of fixed size sliding window, determine the window size by looking at what property of the problem leads to a solution. e.g in [Minimum Swaps to Group All 1's Together](https://leetcode.com/problems/minimum-swaps-to-group-all-1s-together/description/) we count the total number of 1's in the array and use it as sliding window size.
- Sometimes reduces the complexity from $O(n^2)$ to $O(n)$.
- Can be used to find number of sub-arrays with sum at most equal to some $K$.
- Is commonly combined with [[Two-Pointer]] technique.
- When solving problems like *No. Of sub-arrays with $Property = K$* We can use the principle
	- Exactly `K` times = at most `K` times - at most `K - 1` times
	- [Count Number of Nice Subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays/)
	- [Subarrays with K Different Integers](https://leetcode.com/problems/subarrays-with-k-different-integers/)
- Another possible pattern while solving problems like above is to keep a count of the number of sub-arrays that satisfied the property before. And on each iteration we consider those to be added to final answer. e.g [Number of Substrings Containing All Three Characters](https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/)

```rust
pub fn index(c: char) -> usize {
	c as usize - 'a' as usize
}

pub fn number_of_substrings(s: String) -> i32 {
	let mut count = [0usize; 3];
	let s = s.chars().collect::<Vec<char>>();
	let mut ans = 0;
	let mut lo = 0;
	// Counter to keep track of the number of subarrays that contain all three characters while the window removes those elements from itself
	let mut cnt = 0;
	s.iter().enumerate().for_each(|(i, &c)| {
		count[Solution::index(c)] += 1;
		while count.iter().all(|&num| num > 0) {
			count[Solution::index(s[lo])] -= 1;
			lo += 1;
			cnt += 1; // increment the counter for each window that satisfies the condition
		}
		// Add the count to the answer, doing this actually means "Hey, we added a new element to the window which may or may not satisfy the property but it can be paired with all the windows that came before it to make it definitely satisfy the property"
		ans += cnt; 
	});
	ans
}
```
Practice this concept by trying to implement it for [Count Number of Nice Subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays/).

- Sliding Window doesn't mean the window has to always slide. Window is moved and resized dynamically based on whether the elements currently inside the window satisfy our constrains. e.g In the question [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/) we resize/move the window when the window has more distinct characters than the limit $K$.
