[[String]] comparisons using brute force takes $O(min\{n1,n2\})$, where n1 and n2 are sizes of two strings say s and t. Hashing these strings to an integer and comparing those instead of strings brings down the time complexity to $O(1)$. 

If two strings are equal then their hashes have to be equal but if the hashes of two strings are equal, then the two strings need not be equal. So  using hashing will not be 100% deterministically correct, because two complete different strings might have the same hash (the hashes collide). However, in a wide majority of tasks, this can be safely ignored as the probability of the hashes of two different strings colliding is still very small. And we will discuss some techniques on how to keep the probability of collisions very low.

# Calculating the hash function of a string

The good and widely used way to define the hash of a string  $s$  of length  $n$  is

![[stringhash.png]]
where  $p$  and  $m$  are some chosen, positive numbers. It is called a polynomial rolling hash function.

It is a reasonable choice to make p a prime number roughly equal to number of characters in the input alphabet. For example, if the input is composed of only lowercase letters of the English alphabet, p =31 (for lower case characters only).

A  good choice for m is some large prime number like $m = 10^9+9$ .

Example code on how to calculate hash of a string s:- 
```c++
long long compute_hash(string const& s) {
    const int p = 31;
    const int m = 1e9 + 9;
    long long hash_value = 0;
    long long p_pow = 1;
    for (char c : s) {
        hash_value = (hash_value + (c - 'a' + 1) * p_pow) % m;
        p_pow = (p_pow * p) % m;
    }
    return hash_value;
}
```
***Computing the powers of p before hand can boost performance.***


# Applications of String Hashing

- [[Rabin Karp Algorithm]] for pattern matching in a string in $O(n)$ time.
- Calculating the number of different sub-strings of a string in  $O(n^2)$ .
- Calculating the number of palindromic sub-strings in a string.

# Reducing the collision probability

Probability of collision happening is near about $1/m$. For  $m = 10^9 + 9$  the probability is  $\approx 10^{-9}$  which is quite low. But if we did large comparisons we might start getting collisions and our algorithm will return wrong result. 

To fix it we can just compute two different hashes for each string (by using two different  $p$ , and/or different  $m$ , and compare these pairs instead. If  $m$  is about  
$10^9$  for each of the two hash functions than this is more or less equivalent as having one hash function with  $m \approx 10^{18}$ . When comparing  $10^6$  strings with each other, the probability that at least one collision happens is now reduced to  $\approx 10^{-6}$ .
