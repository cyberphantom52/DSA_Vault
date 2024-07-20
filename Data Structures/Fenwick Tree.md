---
tags:
  - datastructure
---
A data structure that supports sum range queries as well as setting values in a static array and getting the value of the prefix sum up some index efficiently.

# Time Complexity:

- Update: $O(\log n)$
- Query: $O(\log n)$
- Construction: $O(n)$

# Advantages

- Efficiently updates elements and calculates prefix sums in logarithmic time.
- Useful for scenarios requiring frequent updates and prefix sum queries.
- Less complex implementation compared to segment trees while providing similar functionalities for specific operations.

# Disadvantages

- Limited to operations that involve prefix sums; not as versatile as segment trees.
- More complex than simpler data structures like arrays or linked lists.
- Requires understanding of binary operations for implementation and usage.

# Applications

- Range sum queries.
- Inversion count in arrays.
- Cumulative frequency tables.
- Used in scenarios where efficient querying and updating of prefix sums are required.

# Working
![[Screenshot from 2024-07-16 15-04-34.png]]
### What about if we want to update our initial array with some new value?
*A prefix sum array is great for static arrays, but takes O(n) for updates.*

![[Screenshot from 2024-07-16 15-51-13.png]]

![[Screenshot from 2024-07-16 15-09-41.png]]

# References

- https://www.youtube.com/watch?v=RgITNht_f4Q
- https://en.wikipedia.org/wiki/Fenwick_tree
- https://cp-algorithms.com/data_structures/fenwick.html

# Questions to practice

- https://www.geeksforgeeks.org/problems/inversion-of-array-1587115620/1
- https://leetcode.com/problems/the-skyline-problem/description/
- https://leetcode.com/problems/count-of-range-sum/description/
- https://leetcode.com/problems/reverse-pairs/description/
- https://leetcode.com/problems/number-of-longest-increasing-subsequence/description/
- https://leetcode.com/problems/queue-reconstruction-by-height/description/