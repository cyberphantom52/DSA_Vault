A data structure that stores data in non contiguous memory as well as a pointer that points  to the next node in the sequence.

## Time Complexity:
- Lookup: $O(n)$
- Set: $O(n)$
- Search: $O(n)$
- Insertion / Deletion : $O(1)+\text{Search time}$
- Insert at tail: $O(n)$
- Insert at head: $O(1)$

# Advantages:
- Dynamic in nature that means we don't need to know the size of data to be stored in advance.
- Can be used to implement other data structures such as [[Stack]], [[Queue]], [[Hash Map]] and [[Tree]].
- In operating systems, they can be used in Memory management, process scheduling and file system.

# Disadvantages:
- Waste some memory because we also need to store pointer along with data.
- There is no random access of elements.
- Cannot traverse backwards (can traverse in doubly-LL).
