---
tags:
  - datastructure
aliases: []
---

An array is a collection of items of same data type stored at contiguous memory locations.

## Time Complexity:
- Lookup: $O(1)$
- Set: $O(1)$
- Search (unsorted): $O(n)$
- Search (sorted): $O(log(n))$
- Insert: $O(n)$
- Delete: $O(n)$
- Append: $O(1)$
- Prepend: $O(n)$

# Advantages
- Any random element can be accessed in $O(1)$.
- Used as a base for implementing other data structures like [[Vector]], [[Stack]], [[Queue]].
- Better locality caching as it's stored in contiguous memory location.
- Better performance as fixed size array is stored in stack memory.
# Disadvantages
- Wastes memory if the allocated space is not fully utilized.
- Can't store multiple data types in same array.
- Can't be used for data whose size is not known ahead of time. (There's a penalty for growing an Array)