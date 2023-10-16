Asymptotic Notation is _used to describe the running time of an algorithm_. When an algorithm consists of many parts, we describe its runtime based on the slowest part.
# Big O Notation
* Describes the worst-case running time of a program.
* If a running time is ‍ $O(f(n))$, then for large enough ‍ $n$, the running time is at most ‍ $k*f(n)$ for some constant ‍ $k$.
![[big-O.png]]
* If a function $f$ is always smaller than a function $g$, i.e $f(n) \leq k.g(n)$. We can say that $f(n)$ is $O(g(n))$
**NOTE:** Big-O doesn't necessarily have to be tightest upper bound.
# Big-$\ohm$ Notation
* Describes the best running time of a program.
* If a running time is ‍$\ohm(f(n))$, then for large enough ‍ $n$, the running time is at least ‍ $k * f(n)$ for some constant ‍ $k$.
![[big-omega.png]]
* If a function $f$ is always greater than a function $g$, i.e $f(n) \geq k.g(n)$. We can say that $f(n)$ is $\ohm(g(n))$
**NOTE:** Big-$\ohm$ doesn't necessarily have to be tightest lower bound.
# $\theta$ Notation
- It is computed by counting the number of iterations the algorithm _always_ takes with an input of $n$
- When we say that a particular running time is ‍$\theta(n)$ , we're saying that once ‍ $n$ gets large enough, the running time is at least ‍ $k_1 * f(n)$ and at most ‍ $k_2 * f(n)$ for some constants $k_1$ ‍  and ‍ $k_2$. Here's how to think of ‍ $\theta(n)$:
 ![[big-theta.png]]
 * i.e if $f(n) = O(g(n))$ and $f(n) = \ohm(g(n))$ then $f(n)$ is $\theta(g(n))$ 
 * When we use big-$\theta$ notation, we're saying that we have an **asymptotically tight bound** on the running time.
	 * "Asymptotically" because it matters for only large values of $n$. 
	 * "Tight bound" because we've nailed the running time to within a constant factor above and below.   
# Time Complexity

| Data Structure | Access | Search | Insertion | Deletion | 
|-|-|-|-|-|
| [[Array]] | $O(1)$ | $O(n)$ | $O(n)$ | $O(n)$ |
| [[Stack]] | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ |
| [[Queue]] | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ |
| [[Linked List]] | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ |
| [[Doubly-Linked List]] | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ |
| [[Hash Map\|Hash Table]] | N/A | $O(1)$ | Best: $O(1)$ <br> Worst: $O(n)$ | Best: $O(1)$ <br> Worst: $O(n)$ |
| [[Binary Search Tree]] | Best: $O(log \cdot n)$ <br> Worst: $O(n)$ | Best: $O(log \cdot n)$ <br> Worst: $O(n)$ | Best: $O(log \cdot n)$ <br> Worst: $O(n)$ |  Best: $O(log \cdot n)$ <br> Worst: $O(n)$ |

| Algorithm | Best | Average | Worst | Space | 
|-|-|-|-|-|
| [[Quick Sort]] | $O(n \cdot log \cdot n)$ | $O(n \cdot log \cdot n)$ | $O(n^2)$ | $O(log \cdot n)$ |
| [[Merge Sort]] | $O(n \cdot log \cdot n)$ | $O(n \cdot log \cdot n)$ | $O(n \cdot log \cdot n)$ | $O(n)$ |
| [[Heap Sort]] | $O(n \cdot log \cdot n)$ | $O(n \cdot log \cdot n)$ | $O(n \cdot log \cdot n)$ | $O(1)$ |
| [[Bubble Sort]] | $O(n)$ | $O(n^2)$ | $O(n^2)$ | $O(1)$ |
| [[Insertion Sort]] | $O(n)$ | $O(n^2)$ | $O(n^2)$ | $O(1)$ |
| [[Selection Sort]] | $O(n^2)$ | $O(n^2)$ | $O(n^2)$ | $O(1)$ |

