---
tags: algorithm, searching
---

#### Time Complexity: $O(N)$
#### Space Complexity: $O(1)$

# Code Example

```cpp
int linear_search(int arr[], int size, int key){
    for(int i = 0; i < size; i++){
        if(arr[i] == key){
            return i;
        }
    }
    return -1;
}
```
