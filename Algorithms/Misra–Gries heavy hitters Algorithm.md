Misra-Gries generalizes [[Boyer-Moore Majority Voting Algorithm]] to $\lfloor n / k\rfloor$ majority elements by first finding up to $k$ candidates through _bag reduction_ and validating those candidates against the original list.

**Problem Statement:** Given is a bag $b$ of $n$ elements and an integer $k ≥ 2$. Find the values that occur more than $n / k$ times in $b$. The Misra-Gries algorithm solves the problem by making two passes over the values in b, while storing at most k values from b and their number of occurrences during the course of the algorithm.

A _k-reduced bag_ for bag b is derived from b by repeating the following operation until no longer possible:
- Delete k distinct elements from b. From its definition, a k-reduced bag contains fewer than k different values.

## Basic Working Principle
- Linearly iterate the input and for each element if the element is already present in the bag, increase it's count else add it to bag.
- If the number of elements in bag is $\geq K$. Then convert into a _k-reduced bag_ by decrementing the count of all elements and then removing those for which $count = 0$.
- Iterate the elements of the reduced bag and verify the count in the input.

## Code Example
```rust
/// Proportion of all elements to search for (n/K)
const K: usize = 3;

/// Implement a reducible bag
#[derive(Debug, Default)]
struct Bag {
    bag: Vec<(i32, i32)>,
}

impl Bag {
    pub fn new() -> Bag {
        Default::default()
    }

    pub fn add(&mut self, element: i32) {
        for (value, count) in &mut self.bag {
            if *value == element {
                *count += 1;
                return;
            }
        }
        self.bag.push((element, 1));
    }

    /// Performs bag-reduction through count decrement.
    pub fn reduce(&mut self) {
        for (_, ref mut c) in &mut self.bag {
            *c -= 1;
        }

        // Retain only nonzero-count elements
        self.bag.retain(|(_, c)| *c > 0);
    }

    #[inline]
    pub fn len(&self) -> usize {
        self.bag.len()
    }

    pub fn get(&self) -> &Vec<(i32, i32)> {
        &self.bag
    }
}

pub fn majority_element(nums: Vec<i32>) -> Vec<i32> {
    let mut bag = Bag::new();
    
    // Find candidate hitters through bag-reduction
    for num in &nums {
        bag.add(*num);

        if bag.len() >= K {
            bag.reduce();
        }
    }

    bag.get()
        .iter()
        .filter_map(|&(e, _) | {
            if nums.iter().filter(|&&g| e == g).count() > nums.len() / K {
                Some(e)
            } else {
                None
            }
        })
        .collect()
}
```