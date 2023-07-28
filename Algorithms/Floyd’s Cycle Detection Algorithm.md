---
tag: algorithm
aliases: Hare and Tortoise Algorithm, Fast and Slow Pointer Algorithm
---
Floyd’s Cycle detection algorithm or Hair Tortoise algorithm is used to detect if there is a cycle in a [[Linked List]] and what is the starting point.

## Code Example
```cpp
// ListNode is LeetCode's implementation of a Linked List
bool hasCycle(ListNode *head)
{
    // edge case: head is empty - no cycle
    if (head == NULL || head->next == NULL)
        return NULL;

    // Define slow and fast pointers
    ListNode *slow = head, *fast = head->next;

    // As long as both pointers don't meet...
    while (slow != fast)
    {
        // If fast has reached the end of the list,
        // there is no cycle
        if (fast == NULL || fast->next == NULL)
            return false;

        slow = slow->next;       // slow pointer moves forward 1 step
        fast = fast->next->next; // fast pointer moves forward 2 steps
    }

    // Didn't reach end of list, there was a cycle
    return true;
}
```
The above code only detects *if* there is a cycle in the [[Linked List]], it does not tell us anything about the where the cycle starts. In order to find the start of the cycle we make the following modification to the code
```cpp
ListNode* detectCycle(ListNode* head)
{
	// edge case: head is empty - no cycle
    if (head == NULL || head->next == NULL)
        return NULL;

	// Define slow and fast pointers
    ListNode *slow = head, *fast = head->next;

	// Check for cycle and detect the meeting point of the two pointers
    while (slow != fast)
    {
        // If fast has reached the end of the list,
        // there is no cycle
        if (fast == NULL || fast->next == NULL)
            return NULL;

        slow = slow->next;       // slow pointer moves forward 1 step
        fast = fast->next->next; // fast pointer moves forward 2 steps
    }

    // Find the start of the cycle
    slow = head; // Reset slow pointer to the head
    // Move slow and fast pointers one step at a time
    while (slow != fast) {
        slow = slow->next; 
        fast = fast->next;
    }

    // At this point, slow and fast pointers meet again at the start of the cycle
	// Return the starting node of the cycle
    return slow; 
}
```

## Why does Floyd’s Cycle Algorithm work?


![[floydsll.svg]]
The algorithm uses two pointers, `slow` and `fast`, to detect cycles in a linked list. They meet at a specific node (pink node), and then the `slow` pointer is reset to the head. By moving both pointers one node at a time, the algorithm finds the start of the cycle (green node).


>Let,
>**x** = Distance between the start of the Linked List and the start of the cycle.
>**y** = Distance between the start of the cycle to the point where **slow** and **fast** first meet each other.
>**l** = Total distance(perimeter) of the cycle.

Distance traveled by pointers on meeting is:
- **slow** has covered $x + s*l + y$, $s \gt 0$.
- **fast** has covered $x + f*l + y$, $f \gt 0$.

Since **fast** travels twice the speed of **slow**. it travels twice the distance. So
$$
x + f*l + y = 2(x + s*l + y)
$$
On solving we get
$$
x + y = (f - 2s)*l
$$
Let $f-2s = k$. Where $k$ is some integer. So
$$x - k*l - y$$
Now, if we move **slow** to the start of [[Linked List]], it will have to cover distance $x$ to meet **fast**, which needs to cover a distance $kl-y = x$. Since both **fast** and **slow** will cover $x$, they'll both meet again at the start of the cycle.