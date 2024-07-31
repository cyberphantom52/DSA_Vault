---
tags:
  - datastructure
---
A heap is a [[Binary tree]]-based data structure that satisfies the heap property: the value of each node is greater than or equal to the value of its children. This property makes sure that the root node contains the maximum or minimum value (depending on the type of heap), and the values decrease or increase as you move down the tree.

## Types of Heap

- **Max Heap:** The root node contains the maximum value, and the values decrease as you move down the tree.
- **Min Heap:** The root node contains the minimum value, and the values increase as you move down the tree.

## Time Complexity:

- Search: $O(n)$
- Insertion: $O(log(n))$
- Deletion: $O(log(n))$
- Heapify: $O(log(n))$
- Get Min/Max value: $O(1)$
- Build Heap: $O(n)$
- Heap Sort: $O(nlog(n))$

## Heap Properties:
- If Heap size = N, then range of leaf nodes is ⌊N/2⌋ to N-1 and range of internal nodes is 0 to ⌊N/2⌋ - 1. (For a complete binary tree).
- If parent = i, then Lchild = 2i+1 and Rchild = 2i+2.
- if Lchild = i or Rchild = i, then parent is ⌊i/2⌋.

## Heap Operations: (Max heap considered)

- **Insertion**: Let's say that the node to be inserted is X. We first place X at the last vacant place in a heap. Continue comparing and swapping with parent till parent with larger value is found.
- **Deletion**: We can delete only the root element in a heap. We first remove the root element an replace it with the last element in the heap. Now we compare this last element which is now the root node with it's children till we find it's appropriate position.
- **[[Heap Sort]]**: We delete element and send the replaced element to the last space at heap and reduce the heap size. After n iterations we would have a sorted order of all n elements.
- **Create Heap**: Insert all elements one by one. After each insertion compare with parent and swap element is greater than parent.  
- **Heapify**:  A procedure for creating a heap. Instead of sending root to bottom we change the direction from leaf to root. 

**Q.** *Now the question may arise that if time complexity of heapify is O(log(n)) then why Build heap has a time complexity of O(n) when it should have been O(nlog(n)).*

We can derive a tighter bound by observing that the running time of **Heapify** depends on the height of the tree ‘h’ (which is equal to lg(n), where n is a number of nodes) and the heights of most sub-trees are small. The height ’h’ increases as we move upwards along the tree. Line-3 of **Build-Heap** runs a loop from the index of the last internal node (heapsize/2) with height=1, to the index of root(1) with height = lg(n). Hence, **Heapify** takes a different time for each node, which is:

For finding the Time Complexity of building a heap, we must know the number of nodes having height h. For this we use the fact that, A heap of size n has at most ![\left \lceil \frac{n}{2^{h+1}} \right \rceil](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-93e2cbe29a5db3d89ba0b36a95c051f9_l3.svg "Rendered by QuickLaTeX.com")nodes with height h. 

To derive the time complexity, we express the total cost of **Build-Heap** as-

 ![T(n) = \sum_{h = 0}^{lg(n)}\left \lceil \frac{n}{2^{h+1}} \right \rceil * O(h)= O(n * \sum_{h = 0}^{lg(n)}\frac{h}{2^{h}})= O(n * \sum_{h = 0}^{\infty}\frac{h}{2^{h}})](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-c7fc53335257718f9b60744a47bfe407_l3.svg "Rendered by QuickLaTeX.com")

Step 2 uses the properties of the Big-Oh notation to ignore the ceiling function and the constant 2(![2^{h+1} = 2.2^h](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-d7927b57333d903f2d5cd256cd3ca83d_l3.svg "Rendered by QuickLaTeX.com")). Similarly in Step three, the upper limit of the summation can be increased to infinity since we are using Big-Oh notation. Sum of infinite G.P. (x < 1)

 ![\sum_{n = 0}^{\infty}{x}^{n} = \frac{1}{1-x}](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-b229149eefb582fbdbbf2576703a1af1_l3.svg "Rendered by QuickLaTeX.com")

On differentiating both sides and multiplying by x, we get

 ![\sum_{n = 0}^{\infty}n{x}^{n} = \frac{x}{(1-x)^{2}}](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-dcb70093965952cb94498bd15ecc0a3c_l3.svg "Rendered by QuickLaTeX.com")

Putting the result obtained in (3) back in our derivation (1), we get

 ![= O(n * \frac{\frac{1}{2}}{(1 - \frac{1}{2})^2})= O(n * 2)= O(n)](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-d762404e1488ca1925b432eff9025177_l3.svg "Rendered by QuickLaTeX.com")

Hence Proved that the Time complexity for Building a Binary Heap is ![O(n)](https://www.geeksforgeeks.org/wp-content/ql-cache/quicklatex.com-9567d404baff2c322642ed8e476ad1af_l3.svg "Rendered by QuickLaTeX.com").


## Applications of Heap

- Used to implement priority queues.
- Used for sorting.
- Used in graph algos like [[Prims Algorithm]], [[Dijkstra's Algorithm]] and A* algorithm.
- Used in load balancing.

## When to use Heaps

- Implementing Priority Queue.
- Find Kth smallest or largest element.
- Median finding problems.